---
title: "Help needed with MathCad 11 (WINE)"
date: 2006-02-10
forum: Desktop Environments
---

### Post by johso on 2006-02-10
Hi people.

I've been trying for quite some time to get MathCad 11 working in Ubuntu. The reason for my struggle is that I have to use for educational purposes, since we use it everyday in our math classes.
So--as I'm sure you'll  all understand--I'd rather be able to ditch my Windows installation (because MathCad is, quite frankly, the only thing holding me back) and be able to actually enjoy life. ;)

So, I found this page: [http://frankscorner.org/index.php?p=mathcad11](http://frankscorner.org/index.php?p=mathcad11) and thought that all my problems were solved. I was wrong.
Unfortunately, Frank is using an older version of WINE, and I have been told by one of my classmates (a Debian lover) that he tried to get it working with the version Frank was using, but without luck. For your information, he hasn't been able to install MathCad 11 either.
These overrides Frank is talking about, I'm not sure what to do with them, since the WINE developers have chosen to ditch the WINE config file. I've put them in the DLL Overrides box in winecfg (libraries tab), but I'm not sure if that's the right place.
When I run "WINEDLLOVERRIDES="ole32,oleaut32,rpcrt4=n" LANG=en_US wine /media/cdrom/Setup.exe"(1) it stalls for some minutes, and then launches the installer window which is filled with a white background (and nothing more). If I just leave it at that, it mostly quits eventually, but as I'm sitting here writing it has been stalling for approximately half an hour. Nothing more seems to happen.

One of my suspects is the internet connection - I think that WINE might be having troubles with establishing a useful connection.
I know that MathCad requires Internet Explorer 5 or higher, and therefore I have also tried to find a solution to install IE6, which is on the CD. But I can't find a description on how I do it; just some programs/scripts that can do it for me, and not install it in the ~/.wine/drive_c/ folder, and then it's useless, since MathCad won't find it.

WINE output:
[lzeus-04xjol/johso] ~ > WINEDLLOVERRIDES="ole32,oleaut32,rpcrt4=n" LANG=en_US wine /media/cdrom/Setup.exe
fixme:urlmon:InternetProtocolSink_ReportResult (0x7fe1d120)->(800c0005 123 (null))


Folks, any help would be appreciated. If you can see anything that I've done wrong; please, do not refrain from telling me.

P.S. Alternatives to MathCad is not my first priority, because that means I have to learn it; know it inside out. Since my teacher shows us how to do things in MathCad, I'm sure you can see that this could get quite impossible to handle.
But; I'm open to suggestions if it is not to complicated an application.

(1) I'm using danish keyboard layout, and for this reason I've put the LANG=en_US string in, to suppress this error: "Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.".

---

### Post by x-eye on 2006-06-19
hi

I have the same problem, found this:

[http://dhost.info/doberski/mcd-tutorial/](http://dhost.info/doberski/mcd-tutorial/)

but I'm stuck at the ```
$ wine EnterpriseWizard.exe
```

until i get it working I use a combination of Openoffice.org Writer and [Graph]("http://padowan.dk/graph/"), wich runs perfecly under Ubuntu.

Right now I'm using wine 9.5 configured with WineTools.

---

### Post by johso on 2006-06-19
Hi!

I got Mathcad working eventually, but I cheated (I used Crossover Office instead). Worked like a charm when I just did it the right way. I've finished my second year now, though, and thus my mathematics class.

But eh, what's the output in your terminal when you execute that command?

---

### Post by x-eye on 2006-06-22
Well, the version I've got is by the way the "Workstation" one.
Don't the difference but the name is WorkstationWizard.exe instead of EnterpriseWizard.exe.

But I got no output :confused: , just a lot of loading and nothing happens.
Sometimes after some minutes, my interface crashes, can't figure out what's happening..

---

### Post by kakk on 2006-11-22
Any ideas, if it is possible to make Mathcad 13 run under linux? When I follow the instructions as shown in [http://dhost.info/doberski/mcd-tutorial/](http://dhost.info/doberski/mcd-tutorial/) I can start the install, but then it requires something like "microsoft .net framework" and thats it. And wine does not seem to support the latter one. Are the Mathcad versions 11 and 13 really so different?

---

