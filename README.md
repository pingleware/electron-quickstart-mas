# electron-quickstart-mas

**Starter app to test building for the Mac App Store.**

This is the electron-quick-start app (see https://github.com/electron/electron-quick-start) set up to be built for the Mac App Store.

This app goes along with the tutorial https://www.techandstartup.com/tutorials/release-electron-app-on-mac-app-store (apparently this tutorial no longer exists)

**Steps to build this app for the mac app store:**

- Load the development dependencies electron and electron-builder: `npm install`
- Run it in dev mode to make sure it works: `npm run start`
- Add your own MacAppStore.provisionprofile to the build directory by creating a new Identifier followed by a new Profile.
- Add your own TeamID.appID in the entitlements.mas.plist file on line 9.
- In the package.json file at a minimum change the name and appId properties to your information.
- Build the app for the mac app store: `electron-builder --mac`
- To deploy to the MacSrtore, you need to create an new App (call it Quickstart by YOURNAME) and replace the productName in package.json with the name of your App.

**To build a Development version of this app (for testing) make the following changes:**

- Add your own AppleDevelopment.provisionprofile to the build directory.
- Make the following changes to the package.json file:
  - Change "target": "mas" to "target": "mas-dev".
  - Change "type": "distribution" to "type": "development".
  - Change "provisioningProfile": "build/MacAppStore.provisionprofile" to "provisioningProfile": "build/AppleDevelopment.provisionprofile".

## Deployment Issues

While Transporter uploaded and was able to execute Deliver, received the following issues on the first attempt,

```
Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (Plugin).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (Plugin)' must be signed with the certificate that is contained in the provisioning profile. (ID: 2031cfe5-fcf6-4597-aa56-7905dcb46a1b)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libvk_swiftshader.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: f2142104-d9aa-40d2-ad39-faf8ff2de628)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libswiftshader_libEGL.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 7ac7c6d2-bafa-4e98-acb8-d141901026f4)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Library/LoginItems/Quickstart by PINGLEWARE Login Helper.app/Contents/MacOS/Quickstart by PINGLEWARE Login Helper' must be signed with the certificate that is contained in the provisioning profile. (ID: 3ecd1555-9f82-4d30-99fc-3b198fee51d9)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/MacOS/Quickstart by PINGLEWARE' must be signed with the certificate that is contained in the provisioning profile. (ID: 90709244-9931-4cd7-882c-34bce6be6b55)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (Renderer).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (Renderer)' must be signed with the certificate that is contained in the provisioning profile. (ID: b15a703f-9bee-4530-92d1-25954e2e8345)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (GPU).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (GPU)' must be signed with the certificate that is contained in the provisioning profile. (ID: 94459c89-43fb-4c64-81af-e8bad1801ab4)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libGLESv2.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 2be99ba6-9d8a-4f06-a825-0d120589e56b)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libswiftshader_libGLESv2.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 22e99810-0011-4f93-93f3-899f6d3129fe)Asset validation failed (90869)
Invalid bundle. The “Quickstart by PINGLEWARE.app” bundle supports arm64 but not Intel-based Mac computers. Your build must include the x86_64 architecture to support Intel-based Mac computers. To support arm64 only, your macOS deployment target must be 12.0 or higher. For details, view: https://developer.apple.com/documentation/xcode/building_a_universal_macos_binary. (ID: 47b75a88-0b87-4d03-857f-41f0f761876f)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libffmpeg.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 319b690a-c298-4f03-9a46-c8881dd7b29f)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper.app/Contents/MacOS/Quickstart by PINGLEWARE Helper' must be signed with the certificate that is contained in the provisioning profile. (ID: 92fe68af-d365-4ad9-91e2-f3c87dab9bdd)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libEGL.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 9cae12d3-2dc9-4676-a7e8-43439e3a8dde)Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Electron Framework' must be signed with the certificate that is contained in the provisioning profile. (ID: 62a16b3f-339c-4a3f-8ae3-f096a81ee296)
```

Adding --uinversal tp the electron-builder command, reduced the issues by one,

```
Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/MacOS/Quickstart by PINGLEWARE' must be signed with the certificate that is contained in the provisioning profile. (ID: 58d88092-08f3-4fb4-93ee-b362aaca6451)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (Plugin).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (Plugin)' must be signed with the certificate that is contained in the provisioning profile. (ID: 346d13be-e83b-43c5-91c0-41812c5f54bf)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (GPU).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (GPU)' must be signed with the certificate that is contained in the provisioning profile. (ID: 75cc91e9-54c2-4484-bdc9-5cc185ec41f2)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libswiftshader_libEGL.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 12817185-eb78-45db-b3df-cef02064421a)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libEGL.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 186d197a-693b-4c17-b723-4d0d30417e8a)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Library/LoginItems/Quickstart by PINGLEWARE Login Helper.app/Contents/MacOS/Quickstart by PINGLEWARE Login Helper' must be signed with the certificate that is contained in the provisioning profile. (ID: 71e1b337-9609-4c97-81c9-7b722130e69e)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libGLESv2.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 75fac776-e54e-43d4-9516-c9da1fd73c60)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper (Renderer).app/Contents/MacOS/Quickstart by PINGLEWARE Helper (Renderer)' must be signed with the certificate that is contained in the provisioning profile. (ID: 53821517-19e4-44e0-8744-203e1c8e59df)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libvk_swiftshader.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 9560b06b-40b9-4abc-ac8a-2463d80dbaf6)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libffmpeg.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: 07ed1f04-c680-409b-a909-5a003f1e4baa)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Quickstart by PINGLEWARE Helper.app/Contents/MacOS/Quickstart by PINGLEWARE Helper' must be signed with the certificate that is contained in the provisioning profile. (ID: 7ed37680-0265-4f8b-bea0-4d8a7097b223)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Electron Framework' must be signed with the certificate that is contained in the provisioning profile. (ID: e85481c3-bd1e-44c7-ac48-8ada03abaa8b)

Asset validation failed (90284)
Invalid Code Signing. The executable 'work.pingleware.quickstart.pkg/Payload/Quickstart by PINGLEWARE.app/Contents/Frameworks/Electron Framework.framework/Versions/A/Libraries/libswiftshader_libGLESv2.dylib' must be signed with the certificate that is contained in the provisioning profile. (ID: ff988f99-6bca-465b-8a38-462372c95a1f)
```
