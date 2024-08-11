# Google Translate (patched)

If you use LineageOS / microG then the Google Translate app might not work properly if the microG companion app (com.android.vending) is installed.. at least, this was my experience.

The solution was to patch the app replacing all `"com.android.vending"` literals with some dummy package like `"com.android.vending0"`.

However, it isn't that easy... the app obviously has to check its signatures which are then probably included in HTTP requests which fail if the signature is not recognized..

I found the class and manually patched the method which calls `toByteArray` method on the `Signature` object to pass the original signature.

## Variants

Since version 7.2, Google Lens is required to be able to translate images.. if you don't want to install that, you can use version 7.1 ~~for a moment~~

## Trust me bro
These APK files are totally trusted and there are no backdoors inside. I know it because they were built by my trusted friend **Jia Tan**, go check him out:
https://github.com/JiaT75

## Let's go

1. Uninstall the Google Translate app which doesn't work (if you've kept it installed for some reason...)
2. Download the patched APKS:
* [**version 8.14**](https://github.com/zb3/google-translate-android-patch/releases/latest/download/translate_814_requires_lens.apk) if you want to use Google Lens
* [**version 7.1**](https://github.com/zb3/google-translate-android-patch/releases/latest/download/translate_old_71_no_lens_required.apk) that doesn't require Google Lens, but it's older
3. Install and enjoy ~~backdoors~~ the app :)

## Disclaimer
These were only tested on LineageOS 21 with microG installed as a normal, unprivileged app and without being signed into a Google account.

## TODO
* Make a patching script instead of patching by hand..
* Find out what actually caused requests to fail with the microG companion app installed - and why it only seems to happen with Google Translate
