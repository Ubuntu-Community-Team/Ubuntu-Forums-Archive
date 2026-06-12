---
title: "Simple CSSM alternative for Xubuntu"
date: 2012-03-03
forum: Desktop Environments
---

### Post by Ikaru on 2012-03-03
I was wondering if there is some alternative for compiz simple CSSM for Xubuntu. I like the option of showing windows/desktop when moving the mouse towards a corner (like in MacOS).

Since the package simple-cssm was removed from the repositories and I failed to install it from a deb file (because of the version of the dependencies) i wanted another alternative.

Thank you

---

### Post by Jose Catre-Vandis on 2012-03-04
Without installing compiz the best you can do is use the "Show Desktop" icon on a panel :(

---

### Post by LewisTM on 2012-03-04
Package brightside offers that possibility.
Install it then run [FONT="Courier New"]brightside-properties[/FONT] to configure the actions for the desired corners.

Cheers!

---

### Post by Ikaru on 2012-03-05
Thanks, brightside did it for "showing desktop".

What about showing all opened windows in tiles like CSSM did? Any thoughts?
I know Ubuntu tweak has that option but since I am using Xubuntu I don't have that option available.

---

### Post by LewisTM on 2012-03-05
Do you mean like the Compiz scale plugin similar to the Mac Exposé feature?
That's possible with Skippy-XD.
A bit more tricky because there is no package for Oneiric.
What I did was grab an [RPM package]("http://mirror.yandex.ru/mandriva/devel/cooker/x86_64/media/contrib/release/skippy-xd-0.5.0-6-mdv2012.0.x86_64.rpm"), made sure I had all [dependencies]("http://rpmfind.net/linux/RPM/mandriva/devel/cooker/x86_64/media/contrib/release/skippy-xd-0.5.0-6.x86_64.html") and extracted the skippy-xd executable to /usr/bin
Then copied the example skippy-xd.rc.default file to ~/.skippy-xd.rc and changed the invoking keysym to Scroll_Lock

I even used Brightside at this point. I set the bottom left corner to execute the custom action
```
xdotool key Scroll_Lock
```
That triggers the tiling feature (You need the xdotool package). 

Of course both skippy-xd and brightside need to be started at logon.

Cheers!

---

### Post by Ikaru on 2012-03-05
> **LewisTM said:**
> Do you mean like the Compiz scale plugin similar to the Mac Exposé feature?
That's possible with Skippy-XD.
A bit more tricky because there is no package for Oneiric.
What I did was grab an [RPM package]("http://mirror.yandex.ru/mandriva/devel/cooker/x86_64/media/contrib/release/skippy-xd-0.5.0-6-mdv2012.0.x86_64.rpm"), made sure I had all [dependencies]("http://rpmfind.net/linux/RPM/mandriva/devel/cooker/x86_64/media/contrib/release/skippy-xd-0.5.0-6.x86_64.html") and extracted the skippy-xd executable to /usr/bin
Then copied the example skippy-xd.rc.default file to ~/.skippy-xd.rc and changed the invoking keysym to Scroll_Lock

I even used Brightside at this point. I set the bottom left corner to execute the custom action
```
xdotool key Scroll_Lock
```That triggers the tiling feature (You need the xdotool package). 

Of course both skippy-xd and brightside need to be started at logon.

Cheers!

Yes, that is the feature I am looking for. I will try it. Thanks

---

