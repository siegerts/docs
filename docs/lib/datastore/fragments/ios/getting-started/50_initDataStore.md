To initialize the Amplify DataStore call `Amplify.add(plugin:)` method and add the `AWSDataStorePlugin`, then call `Amplify.configure()`.

**Add the following imports** to the top of your `AppDelegate.swift` file:

<amplify-block-switcher>

<amplify-block name="Swift Package Manager">

```swift
import Amplify
import AWSDataStorePlugin
```

</amplify-block>

<amplify-block name="CocoaPods">

```swift
import Amplify
import AmplifyPlugins
```

</amplify-block>

</amplify-block-switcher>

**Add the following code** 

<amplify-block-switcher>

<amplify-block name="UIKit AppDelegate">

Add to your AppDelegate's `application:didFinishLaunchingWithOptions` method

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

    do {
        // AmplifyModels is generated in the previous step
        let dataStorePlugin = AWSDataStorePlugin(modelRegistration: AmplifyModels())
        try Amplify.add(plugin: dataStorePlugin)
        try Amplify.configure()
        print("Amplify configured with DataStore plugin")
    } catch {
        print("Failed to initialize Amplify with \(error)")
        return false
    }

    return true
}
```

</amplify-block>

<amplify-block name="SwiftUI App">

Create a custom `AppDelegate`, and add to your `application:didFinishLaunchingWithOptions` method
```swift
class AppDelegate: NSObject, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

        do {
        // AmplifyModels is generated in the previous step
        let dataStorePlugin = AWSDataStorePlugin(modelRegistration: AmplifyModels())
        try Amplify.add(plugin: dataStorePlugin)
        try Amplify.configure()
        print("Amplify configured with DataStore plugin")
    } catch {
        print("Failed to initialize Amplify with \(error)")
        return false
    }

        return true
    }
}
```

Then in the `App` scene, use `UIApplicationDelegateAdaptor` property wrapper to use your custom `AppDelegate`
```swift
@main
struct MyAmplifyApp: App {
    @UIApplicationDelegateAdaptor(AppDelegate.self) var appDelegate

    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

</amplify-block>

</amplify-block-switcher>
Upon building and running this application you should see the following in your console window:

```console
Amplify configured with DataStore plugin
```
