---
title: "Colorzilla eyedropper NOT working in Firefox 1.5.0.4"
date: 2006-06-28
forum: Desktop Environments
---

### Post by mygravity on 2006-06-28
When I try and use the eyedropper on the [colorzilla]("http://www.iosart.com/firefox/colorzilla/") extension I get the following error in a popup box:

> Installation problem or the Eyedropper mode isn't supported on your platform.
You can go to the ColorZilla Home Page to see if your platform is supported.
If so, try-re-installing the extension.
ColorPicker and other features will still work.

I have emailed the author to report the problem, and also have libstdc++5 installed as required.

Does anyone know how to resolve this?

I'm using Ubuntu 6.06 with all updates installed and Firefox 1.5.0.4.

TIA

Andrew

---

### Post by Treviño on 2006-07-19
Same here... bug is still present in kubuntu dapper :(
That's maybe due to Ubuntu firefox build: [https://addons.mozilla.org/comments.php?app=firefox&id=271&left=10&orderby=](https://addons.mozilla.org/comments.php?app=firefox&id=271&left=10&orderby=)

---

### Post by mmcmonster on 2006-07-19
(Edited out due to my not reading...:-) )

---

### Post by reclusivemonkey on 2006-07-19
Whilst its fixed, you can try GColor2; its in the repos.

[http://gcolor2.sourceforge.net/](http://gcolor2.sourceforge.net/)

---

### Post by stengah on 2006-08-15
Same problem/message here. I'm not too familer with what might be the issue, so I've fumbled a bit in the darkness to get it to work. I have tried the following:

**1.** Complete reinstall of firefox following this guide: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and reinstalling the pluging.

Result: No improvement, same output when I try to use Colorpicker.

**2.** I tried this as well (advised by a kind spirit at the extension page)

1. Uninstall ColorZilla if instaled.
2. Download the official firefox binaries from [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)
3. Unpack it to /opt
4. Close firefox.
5. sudo cp /opt/firefox/libxpcom* /usr/lib/firefox/ (copy libxpcom libraries to the instaled firefox)
6. Run firefox then reinstall ColorZilla.

Result: No improvement, same output when I try to use Colorpicker.

**3. **Then I tried another suggestion from another user on the extension page. Seemed to be sensible as well:

$ locate libxpcom
shows files in this directory:
/opt/mozilla/lib/firefox-1.5.0.6/
so just dl and unpack firefox somewhere and
$ cp libxpcom* /opt/mozilla/lib/firefox-1.5.0.6/

*/In my case the output to:*/
$ locate libxpcom
*/is:*/
/usr/lib/firefox/components/libxpcom_compat_c.so
/usr/lib/firefox/libxpcom.so
/usr/lib/firefox/libxpcom_compat.so
/usr/lib/firefox/libxpcom_core.so

making any further efforts in vain as far as I can tell. I've got a feeling that the solution is to do with no. 3, but I really cannot tell:confused: 

Can ANYBODY help?

---

### Post by panas on 2006-08-28
My version 1.5.0.6 


by Ádám Wallner


1. Uninstall ColorZilla if installed.
2. Download the official firefox binaries from [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)
3. Unpack it to /opt
4. Close firefox.
5. sudo cp /opt/firefox/libxpcom* /usr/lib/firefox/ (copy libxpcom libraries to the instaled firefox)
6. Run firefox then reinstall ColorZilla.


i made link to the program in opt just in case
/opt/firefox/firefox

and now works:
 #EAEADA is the color ont the form

---

