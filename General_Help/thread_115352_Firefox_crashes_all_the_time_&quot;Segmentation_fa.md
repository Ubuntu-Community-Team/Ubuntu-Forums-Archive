---
title: "Firefox crashes all the time &quot;Segmentation fault&quot;"
date: 2006-01-10
forum: General Help
---

### Post by jhellen on 2006-01-10
I get Segmentation fault all the time with Firefox. I used PCLinuxOS before and had the same problems there. I'm now using Firefox 1.5 but I had the same problems with 1.07.

What happens if you try to go to [www.unitedlinux.com](www.unitedlinux.com) ?
Mine crashes immediately :(

---

### Post by jhellen on 2006-01-10
I got it fixed :smile: 

/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directoryplugin_get_value 1
plugin_get_value 2
INTERNAL ERROR on Browser End: Exec of "java_vm" failed: 2
<
System error?:: No such file or directory

** (Gecko:9741): WARNING **: Serious fd usage error 24

** (Gecko:9741): WARNING **: Serious fd usage error 22
INTERNAL ERROR on Browser End: Could not read ack from child process
System error?:: Resource temporarily unavailable

...so I just did 'rm /usr/lib/firefox/plugins/libjavaplugin_oji.so'

---

### Post by tenev on 2006-01-10
[QUOTE=jhellen]I get Segmentation fault all the time with Firefox. I used PCLinuxOS before and had the same problems there. I'm now using Firefox 1.5 but I had the same problems with 1.07.

What happens if you try to go to [www.unitedlinux.com](www.unitedlinux.com) ?
Mine crashes immediately :([/QUOTE]

hi - does kubuntu 5.10 come with mozilla firefox browser?

---

### Post by jhellen on 2006-01-11
Well, now I can't remember if Firefox was there after install but I guess you know it already.

I guess you ment that this isn't a Kubuntu issue. I think it's just some Linux plugin issue because I've never seen crashes like these in the Windows-version of Firefox.

Firefox seems to work fine now when I removed that file. (for the moment)

---

### Post by southernman on 2006-01-11
[QUOTE=tenev]hi - does kubuntu 5.10 come with mozilla firefox browser?[/QUOTE]
It isn't installed with kubuntu. Of course you can get it with Synaptic.

---

