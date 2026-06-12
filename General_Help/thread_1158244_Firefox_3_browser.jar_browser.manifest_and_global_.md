---
title: "Firefox 3 browser.jar browser.manifest and global folder."
date: 2009-05-13
forum: General Help
---

### Post by m_2009 on 2009-05-13
Can anyone tell me where the global folder is actually located in firefox in ubuntu, i have searched everywhere yet cannot find it.

```
/usr/lib/firefox-3.0.10/chrome/browser.manifest contains the following.

style chrome://global/content/customizeToolbar.xul chrome://browser/content/browser.css
overlay chrome://global/content/viewSource.xul chrome://browser/content/viewSourceOverlay.xul
override chrome://global/content/license.html chrome://browser/content/license.html
style chrome://global/content/customizeToolbar.xul chrome://browser/skin/
overlay chrome://global/content/viewPartialSource.xul chrome://browser/content/viewSourceOverlay.xul
content browser jar:browser.jar!/content/browser/ xpcnativewrappers=yes contentaccessible=yes
overlay chrome://browser/content/browser.xul         chrome://browser/content/safebrowsing/report-phishing-overlay.xul
```

However the browser.jar contains no such folder, or any of the files references.

I am working on a theme for firefox and want to have the icons shown on all the button in dialog windows such as the "+" on "add new toolbar" in the customize toolbars dialog, and buttons such as OK/Apply which have the green return key symbol in the default themes.

Does anyone know how ic an incorportate all of this into a theme.

---

### Post by LoloftheRings on 2009-05-13
You can download firefox from the mozilla site, giving you the complete application in one directory.

---

### Post by m_2009 on 2009-05-13
I need the complete files for the ubuntu specific version of firefox though with all the ubuntu tweaks that have been applied etc.. as the new theme Im currently making my ain is to have it blend with ubuntu 100% with all the buttons in the dialogues etc...
 
So i need to try and locate the global folder that all the css files are in for the ubuntu release of firefox...
 
If that makes sense?

---

### Post by albert ozzy on 2009-05-13
chrome://global is a relative address. All the files pointed with chrome://global are inside browser.jar. Since you're developing a new theme i suggest you to look inside classic.jar.And definitely here: 
[https://developer.mozilla.org/en/Creating_a_Skin_for_Firefox%2F%2FGetting_Started](https://developer.mozilla.org/en/Creating_a_Skin_for_Firefox%2F%2FGetting_Started)

---

### Post by m_2009 on 2009-05-13
Ive looked in both browser.jar and classic.jar, neither of these archives contain a folder called global as references in the manifests.
 
Are you able to find them folders within either of the .jar files?
 
According to the link you posted, classic.jar should contail a folder called skin, and then subfolders of the following name.
 
skin\classic\browser
skin\classic\communicator
skin\classic\global
skin\classic\help
skin\classic\mozapps (I konw in linux it would be / but i just copied and pasted)
 
My classic.jar only contains the following.
 
skin\classic\browser
skin\classic\communicator
 
and preview.png and icon.png in the archive root...
 
Im totally confused by where these files are located so that i can view them in order to copy the relavent code frmo them.

---

### Post by albert ozzy on 2009-05-13
ooops i didn't pay attention to the files inside your box. Sorry about that. BTW I have them all on file /usr/lib/firefox-3.5b4pre/chrome/browser.jar AND toolkit.jar

---

### Post by m_2009 on 2009-05-13
I just downloaded the deb packages for that verison of firefox from the repositories, and there is still no global folder in browser.jar, or skin.jar.

where exactly are you finding them or seeing them?

---

### Post by albert ozzy on 2009-05-13
i've downloaded ff3b4 from mozilla website and installed. Your file content of chrome://global are in > /usr/lib/firefox-3.5b4pre/chrome/toolkit.jar there's a folder structure like this inside that arcive > /content/global/

---

### Post by m_2009 on 2009-05-13
Yes in the officil mozilla build, but as i said above i need the ubuntu specific version, the one in the repositories that have the additional extras for ubuntu such as the GTK themed dialog buttons etc...

---

### Post by m_2009 on 2009-05-13
Finally found it after hours of searching.

It seems the global folder is actually located in

/usr/lib/xulrunner-1.9.0.10/chrome/classic.jar

Not the firefox folder.

---

