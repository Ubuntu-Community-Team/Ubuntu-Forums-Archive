---
title: "Ubuntu woes ..."
date: 2006-01-03
forum: General Help
---

### Post by wannabelinuxconvert on 2006-01-03
Hi,

This is my first post so please be gentle, and I apologise if I ask some questions already asked many times before but I just can't seem to find the answers I'm looking for.

I've just installed Ubuntu on my Mac Mini (1.42ghz 80gb superdrive) and everything worked fine ... installation, first boot, even mounting my osx drive at bootup (not bad I thought for a complete Linux newbie :D )

I have how ever come across some stumblin blocks and I hope you friendly kind guys here could maybe shed some light !?

1/ Wireless USB dongle

Can anyone please help with the installation of the drivers for my Linksys WUSB54Gv4 !? 

It's based on the RT2500 chipset according to the ndiswrapper pages, so I followed the wiki instructions here on the Ubuntu wiki but to no avail. 

I was originally going to try using the windows drivers and ndiswrapper but apparantley this won't work on ppc distros' !?

I did then stumble at the first hurdle when trying to use the command 'make' as this is apparently an unrecognised command !? 

Does anyone know of any binarys that I could just install, or a complete newbie setup guide (remembering I can't use things like 'apt-get' as I have to access the internet by booting back into osx and using the airport card)

2/ iPod

I was really impressed that when I plugged in my iPod Ubuntu recognised it straight away and mounted it. Even the music player loaded all the tracks, except when I try to play any of them, an exclamation mark appears down the side !?

I did read a post a while back about installing some plugins to make this work but I can no longer find it, can anyone point me in the right direction !?

Also, I've been reading about a product called GTKPod ... is this any good !? Does it support iPod Video !?

3/ Desktop

This may sound really bizarre, but I've seen many Linux desktop screen shots with the recycle bin ... sorry wastebasket  ;) on the desktop, but I can't for the life of me figure out ow to do this ... can anyone please advise !?

4/ Drives

After getting the osx drive to mount at log in, it appears in the drop down menu (thinks it's called places) inplace of the original 'filesystem' one ... is there a way to get both the Linux partition and macosx partition to appear in that menu instead of one or the other !?

Any help on any of these issues would be greatly appreciated by a humble Linux newbie :D 

Thanks in advance

Mic

---

### Post by 23meg on 2006-01-03
[QUOTE=wannabelinuxconvert]
3/ Desktop

This may sound really bizarre, but I've seen many Linux desktop screen shots with the recycle bin ... sorry wastebasket  ;) on the desktop, but I can't for the life of me figure out ow to do this ... can anyone please advise !?
[/QUOTE]
In Applications / System Tools / Configuration editor, check this key: /apps/nautilus/desktop/trash_icon_visible

---

### Post by wannabelinuxconvert on 2006-01-03
If you have been directed here from one of the other threads then this is the correct one so please post your answers here. Sorry about the confusion.


**Thanks 23Meg for the answer, will give it a go and let you know how I get on.**

Mic :p

---

### Post by wannabelinuxconvert on 2006-01-04
Can anyone help with the other questions !?

Mic

---

### Post by manfo on 2006-01-04
[QUOTE=wannabelinuxconvert]
2/ iPod

I was really impressed that when I plugged in my iPod Ubuntu recognised it straight away and mounted it. Even the music player loaded all the tracks, except when I try to play any of them, an exclamation mark appears down the side !?

I did read a post a while back about installing some plugins to make this work but I can no longer find it, can anyone point me in the right direction !?
[/QUOTE]

Perhaps you have to enable support for restricted formats such as mp3. Try to check this page, it should help you: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Bye!
.m

---

### Post by kidcharles on 2006-01-04
> I did then stumble at the first hurdle when trying to use the command 'make' as this is apparently an unrecognised command !?

For some bizzarre reason Ubuntu (and many other distros) don't install compilers and associated utilities by default (gcc, make, etc.) You might try to apt-get install (or use graphical Synaptic Package Manager found under System->Administration) the 'build-essential' package, which will install 'make', 'gcc', and other things. Try this even without access to the internet, as these packages might be on the install CD. I don't know if they are.

---

### Post by hobbit1983 on 2006-01-05
An easier way to get a Trashcan icon is to click on a grey bar (top and bottom of screen) 

Click add to Panel

Select WasteBasket

I'm sorry but I don't know the answer to any of your other questions

---

### Post by nalmeth on 2006-01-05
Regarding your wireless:

"booting back into osx and using the airport card"

is this another wireless card in the same pc with ubuntu?? 
I had extreme difficuties setting up a LinkSys USB wireless adapter for a friend of mine. After searching, digging, and more searching, I found the only result was a company called linuxiant, or a variant thereof.. For the life of me I can't find it right now, and don't have much time to now. Google it with wireless or your wireless-adapter-model-number or whatever. My guess is that it is a driver under a restricted liscence, meaning you won't have it for free. I think it costs 20 bucks for a lifetime, but I find this unreasonable. YOU HAVE ALREADY PAID FOR THE DRIVER!! :rolleyes: 
If its a-ok with you go ahead with it. 

Although I have been using Gnome for some time now, I am still more experienced with KDE. I know that amarok is excellent all around, and will interact with your ipod. Damn I need one soon. I'm still a minidisc user!! :cry: Beyond that, considering my lack of ipodding, all I can suggest is google "ubuntu ipod" <-- this type of search has solved a myriad of issues for me.

Regarding your trash icon, follow the previous recommendation to have it on your toolbar, but I don't find it very appealing. KDE has a nicer trash I think, and no need to change themes to get a decent one. It comes on the desktop, but you can drag it on or off the toolbar.

Hope I didn't forget anything

EDIT:
Have you tried "Easy Ubuntu" or "Automatix" yet? It installs many restricted formats, but I never had trouble with mp3!

---

