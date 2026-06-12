---
title: "Steam installation is an endeavour"
date: 2014-07-19
forum: Gaming &amp; Leisure
---

### Post by tatsujb on 2014-07-19
Hi all.

I attached a screenshot at the bottom


I just freshly installed my ubuntu and I'm right off from testing Manjaro on my usb stick. 

So I was like yeah, Manjaro is great but Ubuntu seems better.

manjaro had steam pre-installed and working on the usb stick.

why doesn't Ubuntu have Steam preinstalled?

why do we even have to add a source to be able to install it in AppStore?

why doesn't it work when i click install in app store?

It's been doing this thing in a loop where it Updates cache five times then installs steam five times but all it does is wait hours then skip each one.

where is this going and once again, let me reiterate, to avoid all of this why isn't steam preinstalled?

Save me. this is freaking ridiculous.

---

### Post by oldrocker99 on 2014-07-19
So go to [http://steampowered.com](http://steampowered.com) and download the Linux client from there, and install it with USC, or gdebi or:

```
sudo dpkg -i steam_latest.deb
```

The reason Steam isn't installed on Ubuntu is that there are a lot of programs that don't come preinstalled, and room has to be kept for the ones that **are** preinstalled. GIMP isn't preinstalled, either. Manjaro preinstalls Steam because it's an Arch derivative, and it's easy for them (not being bound to a CD-sized download) to add Steam, which isn't available except as a .deb file, which Manjaro may or may not be able to install directly.

---

### Post by tatsujb on 2014-07-20
Hi thanks very much I think this will work, I'll post back if it does however : [https://www.google.fr/search?q=USC&oq=USC&aqs=chrome..69i57&client=ubuntu-browser&sourceid=chrome&es_sm=0&ie=UTF-8](https://www.google.fr/search?q=USC&oq=USC&aqs=chrome..69i57&client=ubuntu-browser&sourceid=chrome&es_sm=0&ie=UTF-8)
what's USC

I installed gdebi just in case.

and since I have the terminal command, isn't the terminal command the cleanest?

EDIT :

command line gave : Errors were encountered while processing: steam-launcher

but just clicking on it worked.

---

### Post by oldrocker99 on 2014-07-20
Oh, USC is the Ubuntu Software Center; sorry for the acronym. And it's preferable to use the terminal whenever; IMHO. It's just a matter of learning the commands, which is easy when you search.

---

### Post by tatsujb on 2014-07-20
> **oldrocker99 said:**
> Oh, USC is the Ubuntu Software Center; sorry for the acronym. And it's preferable to use the terminal whenever; IMHO. It's just a matter of learning the commands, which is easy when you search.
alright well thanks, this matter is now solved and you did it singlehandedly, many many kudos.

do you have any ideas on my Grooveshark/flash/pin issue? : [http://ubuntuforums.org/showthread.php?t=2235293](http://ubuntuforums.org/showthread.php?t=2235293)

---

### Post by oldrocker99 on 2014-07-20
My pleasure, and I replied to that thread.

---

### Post by mastablasta on 2014-07-21
> **tatsujb said:**
> 

why doesn't Ubuntu have Steam preinstalled?

.

Ubuntu is aimed at enterprises as well as home users. in fact it's the enterprises that provide the money for further development. 

now i assume the enterprises are not too thrilled to have gaming platform installed by default nor do they need it. however it could be in the official repositories and maybe it will be later on if it's not yet.



there is a gamers version of ubuntu i believe (a respin which now porbabyl also has it preinstalled). in any case i see oyu solved it.

---

