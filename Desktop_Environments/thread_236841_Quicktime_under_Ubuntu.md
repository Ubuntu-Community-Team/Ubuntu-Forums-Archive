---
title: "Quicktime under Ubuntu"
date: 2006-08-15
forum: Desktop Environments
---

### Post by aie on 2006-08-15
I am trying to install QT under ubuntu.
During the process, it required that I install gcc.

While installing gcc, i got the following error message :
 cc: command not found
*** The command 'cc -o conftest -g   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.

Is there any workaround this problem ?
or is there an easier way to install QT ?

Many thanks

---

### Post by win_zik on 2006-08-15
To install gcc, make, etc, simply install build-essential.

About quicktime, what exactly are you trying to do? If you want to simply watch quicktime movies take a look at the wiki:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope this helps!

---

### Post by tcollogne on 2006-08-15
If you follow this link, it should work. This helps you install multimedia codecs, including quicktime codec.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

Hope this helps

---

### Post by aie on 2006-08-15
I am trying to view inside mozilla QT movies.
It tells me that the plugin is missing and (there is no plugin of course for neither Windows Media nor Quicktime)

I have Totem installed and am able to view mpeg movies without any trouble.

I am looking into the links you have sent and will try and find an appropriate solution

---

### Post by aie on 2006-08-15
ok.
the link on the restricted formats was more helpful.

I installed the w32 codecs as described:
wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)

sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

but am not able to install the totem-gstreamer-firefox-plugin. The package installer is giving me the following error:

Dependency is not satisfiable.

Thanks for the two previous leads.

*edit*
Nevertheless, in the second link i had the clue to install the plugin

sudo apt-get install totem-gstreamer-firefox-plugin

---

### Post by win_zik on 2006-08-15
In my experience totem with the xine backend supports more formats.
Simply try it out by installing totem-xine totem-xine-firefox-plugin and libxine-extracodecs.

A good, maybe even supperior plugin especially when it comes to viewing HD trailers on the Apple site is the mplayerplug-in. The package is called mozilla-mplayer. So if totem doesn't work, maybe give this one a try.

Hope this helps.

---

### Post by Yizi on 2007-08-28
> **aie said:**
> I am trying to view inside mozilla QT movies.
It tells me that the plugin is missing and (there is no plugin of course for neither Windows Media nor Quicktime)

I have Totem installed and am able to view mpeg movies without any trouble.

I am looking into the links you have sent and will try and find an appropriate solution

i have exactly the same problem anyone can help?:(

---

