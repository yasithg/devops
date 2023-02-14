# devops

## Android Continues Deployment (CICD)

  `Android_Deployment.yml` file inside github workflows contains CICD implementation of Android deployment process.

### Version Update

  We need new version code on each release there for we use [chkfung/android-version-actions](https://github.com/chkfung/android-version-actions). Each workflow run we get workflow number and assign it as `Version Code`.

### Install node modules

 Before we run the project we need to install node modules.

### Run Tests (CI)

  Before we build the project make sure there are no errors. 
  
### Setting up Gradle cache

  We will cache our Gradle dependencies and wrapper to keep our builds faster. For that We use Github cache actions.
  
### Make Gradle executable

  Some Linux environments, Gradle is not executable by default. Just in case We make sure it's execuatable.
  
### Generating the Android release build

  This part is bit tricky. We need `ANDROID_SIGNING_KEY`, `ANDROID_SIGNING_ALIAS`, `ANDROID_SIGNING_STORE_PASSWORD` and `ANDROID_SIGNING_KEY_PASSWORD`.

  - _ANDROID_SIGNING_ALIAS_ : Alias name you provide when you create the `Key`.
  - _ANDROID_SIGNING_STORE_PASSWORD_ : Password you provide as store password when you create the `Key`.
  - _ANDROID_SIGNING_KEY_PASSWORD_ : Password you provide as key password when you create the `Key`.
  - _ANDROID_SIGNING_KEY_ : Base 64 encorded `signing key` In order to convert your releaseKey.jks to base64 encoded one you gonna need `Openssl`.
    wirh below commant you can create your base64encoded key file.
   ```openssl base64 < some_signing_key.jks | tr -d '\n' | tee some_signing_key.jks.base64.txt```
