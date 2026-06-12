---
title: "Self-contained firefox"
date: 2009-01-22
forum: General Help
---

### Post by Chops II on 2009-01-22
Hi there,

Am trying to develop for the Mobile Web, and this requires that i use User-Agent switcher in Firefox3. For this to work, most of the time that requires that i close all instances of the browser. I was just wondering if i can make a completely separate and self-contained copy of firefox that i can change the user-agent and restart all the time without having to close all of my windows?

Thanks a bunch for any useful responses, or even ones that are just trying to be helpful, of course;).

Chops II

---

### Post by Chops II on 2009-01-22
Can someone please help me with this?

---

### Post by mssever on 2009-01-22
Can't you just edit the user agent string in about:config?

Also, if you start Firefox thus: ```
firefox -ProfileManager
```you'll be able to configure separate profiles with independent settings. See ```
firefox --help
```for other options.

---

### Post by Chops II on 2009-01-22
Thanks for your response.

A couple of issues with that suggestion:
Changing the user agent string requires a restart of firefox. The reason i posted this thread was to find out if there was a way of doing it without having to close windows that i want to leave open, such as a window for my Gmail and things like that. I dont want to have to go around opening everything up and arranging my windows how i like then everytime i want to change user-agent, because i will be having to do it quite often. 
Also i will be needing to use the plugin rather than just about:config because the user agent strings i need to use are quite large and specific being that i'm trying to pretend to be different mobile phones.

The idea about using -ProfileManager, ive never used that before, does it let you run multiple profiles concurrently (in different windows of course)? if so, and i can set up different profiles with different user-agent strings then that might be a solution.

---

### Post by mssever on 2009-01-22
> **Chops II said:**
> Changing the user agent string requires a restart of firefox.Really? I guess that's another case of Firefox's annoying habit for requiring restarts all the time. I hate that. You'd think that a change as simple as changing the user agent string could be made on the fly. Opera can do that. As you can tell, I've never tried this in Firefox.

> The idea about using -ProfileManager, ive never used that before, does it let you run multiple profiles concurrently (in different windows of course)? if so, and i can set up different profiles with different user-agent strings then that might be a solution.
Try it and see. I imagine you can, at least if you use the -p option. But I haven't used multiple profiles since Netscape 4 on Windows, so I have no idea how much has changed since then. That's been, what, 11 years?

---

### Post by Chops II on 2009-01-22
> **mssever said:**
> Really? I guess that's another case of Firefox's annoying habit for requiring restarts all the time [...] Opera can do that. 


Does Opera let you add arbitrary user-agent strings? If so that could well also be a solution.

---

### Post by mssever on 2009-01-23
> **Chops II said:**
> Does Opera let you add arbitrary user-agent strings? If so that could well also be a solution.
It doesn't appear that way, but I don't know Opera very well. The configuration setting is [here]("opera:config#UserAgent%7CAllowComponentsInUAStringComment"), and the help page is [here]("http://www.opera.com/support/usingopera/operaini/#ua").

---

### Post by dagnabit dang doohickey on 2009-01-23
Multiple instances of Firefox can be run side-by-side using separate profiles.

1. Create a new profile folder:
```
cd ~/.mozilla/firefox
mkdir mobile.profile

```2. Make a backup of your current profiles.ini file:
```
cp profiles.ini profiles.ini.backup

```3. Edit profiles.ini to include the new profile folder. In the following example the italicized text should be replaced with the Name and Path of your default profile found in your current profile.ini:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=*Default*
IsRelative=1
Path=*default.default*
Default=1

[Profile1]
Name=Mobile
IsRelative=1
Path=mobile.profile

```
4. Launch Firefox using this new profile with the following command:
```
firefox -no-remote -P Mobile

```

Here are a couple of links that may come in handy:
[http://kb.mozillazine.org/Profiles.ini_file]("http://kb.mozillazine.org/Profiles.ini_file")
[http://kb.mozillazine.org/Command_line_arguments]("http://kb.mozillazine.org/Command_line_arguments")

---

### Post by mazato on 2009-01-23
Hey there Chops II:
In my desktop I have like 3 different profiles of firefox that I set some time ago for the purposes of testing.
You can run all those 3 different profiles at the same time.
First create the profiles using the ProfileManager.
Once you do that you can create shorcuts to each profile like this:

Profile #1 shorcut: "firefox -P #1 -no-remote"
Profile #2 shorcut: "firefox -P #2 -no-remote"
Profile #3 shorcut: "firefox -P #3 -no-remote http://www.google.com"
Now the interesting part here is that if you don't use the -no-remote argument then the next window of firefox that you open is going to be the same profile of the last one you openned and is running.
Now, I did this some time ago. So don't take my word for it. The only thing I might not be 100% sure is opening other firefox windows without using the mentioned argument.
Try it and you will quickly notice the differences.
Good luck!
P.S. the last example of the shorcuts, opens google using that profile, neat?!

---

### Post by Chops II on 2009-01-23
Thanks everyone, this sounds very promising now.

I will try to remember to let you know how i go, but for now its time for me to leave for Australia Day long weekend!

Have fun everyone

Chops II

---

### Post by Chops II on 2009-01-26
Thanks a bunch everyone, this is pretty much exactly what I needed!

Chops II

---

### Post by mazato on 2009-01-27
Glad it worked..
good luck!

---

