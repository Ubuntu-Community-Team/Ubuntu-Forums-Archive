---
title: "Konqueror view profiles"
date: 2006-01-26
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-26
Up until now I haven't much liked Konqueror as a file manager, but I've just read through the manual again, and have realised a few things that might make a difference.  Firstly, I don't want to use it as a web browser - I simply want to use it as my file browser. If possible I want to disable all web browsing features.

The help file mentions that if you want to use it as a web browser - you use the World Icon shortcut under Internet in the KDE menu, and if you want to use it as a file browser you click Home under the KDE menu. Now I have the internet shortcut icon, but I have no Home shortcut icon anywhere.  Hence I've been opening Konqueror in web browser view all the time.

Does anyone know how I can add that file browsing view shortcut to my KDE menu or my desktop, so that I can see exactly what that view is?  I've been messing about with the web browser view trying to customise it to get the view I want, but if there's already a file browser profile somewhere, it would make sense to at least check that out first. I note that under *Settings* there is a *Save view profile for "web browser"* option, which takes me to a list of about six or seven different view profiles. It doesn't however give you a way to start Konqueror up in one of those profiles.

This is probably something terrible simple that I'm overlooking but if anyone can enlighten me I'd be grateful.  

Many thanks!  :)

---

### Post by Jucato on 2006-01-26
Ok here are some things:

Use this command to start up your konqueror:
1. as a File Manager:
```
kfmclient openProfile filemanagement
```
2. as Web Browser
```
kfmclient openProfile webbrowser
```
You can use this to edit/make links on your menu/desktop

What "web browsing features" do you want to deactivate?

---

### Post by seakiwi on 2006-01-26
[QUOTE=Fenyx]Ok here are some things:

Use this command to start up your konqueror:
1. as a File Manager:
```
kfmclient openProfile filemanagement
```
2. as Web Browser
```
kfmclient openProfile webbrowser
```
You can use this to edit/make links on your menu/desktop

What "web browsing features" do you want to deactivate?[/QUOTE]

Many thanks - that does exactly what I wanted!  :) 

I simply want to use Konqueror as a file manager, not as a web browser. Up until now I haven't been able to access the various view profiles. For some reason the only Konqueror entry in my KDE menu is Web Browser, which opens it into Web Browser profile. 

I've now created a desktop short with your code above and Konqueror now opens for me as a file manager without the web browsing "stuff".  I've made a couple of minor customisations and saved the customised profile so now when I start it, it opens exactly as I want it. Many thanks! O:) 

It's just a matter of personal preference. I just prefer my web browser to be totally separate from my file manager. 

Now, to find an email client for Kubuntu that works with GnuPG plus gives me the features I want. KMail is a nice email client, but it's GnuPG integration totally sucks. I've given up trying to make it work properly. Thunderbird with Enigmail handles the GnuPG stuff flawlessly, but it has a few niggly annoyances, such as no minimize to tray, no .wav capability and one or two other things.  If I manage to stumble across an alternative client that can do all that, I'll be ecstatic ;) 

Thanks again for your help!

---

### Post by Jucato on 2006-01-26
Glad I could help. :D

I also felt the same way before (about separating file managers and web browsers), until I realized: why should I use twice the amount of resources using two programs, when I can use less with just one? Especially, with Firefox, which is quite a resource hog. (Opera just didn't click with me). And after reading this OLD (2004) [article]("http://osdir.com/Article2159.phtml"), I grew to appreciate the way KDE handles this sort of integration, not only with Konqueror, but with the rest of the system.

Oh and btw, no matter what profile you use, you will always be able to access the web. Heck, you can even access the web in amaroK, Kaffeine, and Kate, although with different results (Kate displays source code, amaroK and Kaffeine plays audio/video, etc).

---

