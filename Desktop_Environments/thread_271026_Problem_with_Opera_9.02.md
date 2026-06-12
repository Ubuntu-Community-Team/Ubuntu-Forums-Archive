---
title: "Problem with Opera 9.02"
date: 2006-10-04
forum: Desktop Environments
---

### Post by g0nzo on 2006-10-04
Hi,

I had previous version of Opera installed (9.0 or 9.01) and I downloaded new 9.02 version. I tried to install it, but it said that it can't find libqt3c102-mt package and won't install. Adept said that current Opera installation is broken and removed it. I downloaded libqt3c102-mt package, but during installation it said that libqt3-mt is already installed and can't be removed.

What should I do to install Opera?

---

### Post by Serious Sven on 2006-10-17
Have you tried to enable the multiverse repository?

I enabled it and downloaded the installer which installed the dependencies automatically.

---

### Post by Sef on 2006-10-17
To enable the repositories, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by robenroute on 2006-10-25
Well, I've enabled the repositories (universe, multiverse, backports, the works!) but there's no Opera available....

Am I doing something wrong? BTW, I installed 9.00 through Automatix2 (which is a fantastic tool :))

Thanks, Rob

---

### Post by Ambimom on 2006-10-25
From one opera user to another...why don't you uninstall with Synaptic the opera version and the "missing" libqt3c102-mt.  Mark for complete removal.

Then download directly from the Opera website; and install the latest version by right-clicking the downloaded file.  It should ask you if you want to install.  

The settings et.al. should be okay. 

Worth a try.  I had no problem getting the latest Opera 9.2. version from their website and installing it on Ubuntu.  Of course that doesn't lessen your own frustration.  Getting Opera to perform properly in Ubuntu can be frustrating; but it can be done.  It took me 10 days before I got the java and flash plugin path corrected.

---

### Post by robenroute on 2006-10-25
Well, I did indeed remove 9.00 (and as you suggested, a complete removal (which wasn't a "complete" removal, by the way, as my bookmarks, saved passwords, and other stuff was still being recognized by the new Opera)) and installed the downloaded deb-file: 9.02 working!

Thanks a bunch, Rob

---

### Post by FyreBrand on 2006-10-25
robenroute - if you just want to install Opera and you don't care if it's version 9.0 then you can install it from the repositories.

The repo you want to enable is this:
```
## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

This is from [**Ubuntu Demon's recommended repository list**]("http://www.ubuntuforums.org/showthread.php?t=185758").

@Ambimom - I have flash working okay in Opera 9.0 but I still can't get Java to work right I think even though I've explicitly put a JVM path in the Opera Options.  I can use my Moodle site in Firefox, but not Opera or Konqueror.  It was rather frustrating, but Firefox 2.0 is a vast improvement over 1.5 so I'm okay with it for now.  If you feel like posting what you did to get Java working in Opera please do so.  I would like to see if I've missed a step.

---

### Post by Ambimom on 2006-10-26
Provided that you installed the latest Java plugin (I used Automatix to install it) which I assume you have since it works in Firefox...

In Opera, open Tools/Preferences/Advanced/Content

The plugin path should read:

/usr/lib/firefox/plugins:/usr/lib/opera/plugins

My problem was that the plugin path had links to netscape and mozilla too.  Once I removed those, my problems were solved!  Give it a try.

---

