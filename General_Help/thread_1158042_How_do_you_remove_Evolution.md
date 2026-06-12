---
title: "How do you remove Evolution?"
date: 2009-05-13
forum: General Help
---

### Post by themadhatter on 2009-05-13
I want to remove Evolution. I don't use it (100% webmail). And if I accidently click on an email address, it starts, slowing the system until I can kill it. 

Any good suggestions?

FYI, for those who will suggest that I should just kill the link, I've used Evolution before, and quite frankly hated it. Even if I wasn't using webmail I'd not want it on any computer I own.

Oh, and does anyone know why the hell it appears to be tied into the Gnome desktop? I can't think of any valid reason, and it appears to be a really dumb design choice.

---

### Post by Skripka on 2009-05-13
Last I knew you couldn't remove Evolution without killing your system.  Evolution has as a depend a database integral to the Ubuntu OS.  Remove Evolution and you remove that database and kill your OS.

---

### Post by Simian Man on 2009-05-13
You don't install it in the first place. :/

---

### Post by TheExplorer on 2009-05-13
You can remove it easily via Synaptic (evolution and its plugins), but **DO NOT** remove the following packages as it may screw your system:

1) evolution-data-server
2) evolution-data-server-common
3) evolution-documentation (it's tied up with the language-support packages)

After that you may also uncheck the Evolution Alarm Notifier under System -> Preferences -> Startup Applications.

Actually you are able to remove any package from Gnome, but be attentive while doing it and it's recommended to remove the packages one by one (not in dozens :)), watching if it's not triggering the removal of core packages like ubuntu-desktop etc.

P.S. Gnome itself is an environment which contains a lot of apps by default like mail client, browser etc. to let people get the system up and running with the most needed software. It's a complex solution by the way and it's not that bad. KDE has the same set of software. The other thing is that you may not like this or that application, so you are free to install your prefered one and associate it as the default. It's up to you to decide and it's all free. The thing is: you **should** google a bit and see what is removable and what's not.

---

### Post by themadhatter on 2009-05-14
> **TheExplorer said:**
> You can remove it easily via Synaptic (evolution and its plugins), but **DO NOT** remove the following packages as it may screw your system:

1) evolution-data-server
2) evolution-data-server-common
3) evolution-documentation (it's tied up with the language-support packages)

After that you may also uncheck the Evolution Alarm Notifier under System -> Preferences -> Startup Applications.

Actually you are able to remove any package from Gnome, but be attentive while doing it and it's recommended to remove the packages one by one (not in dozens :)), watching if it's not triggering the removal of core packages like ubuntu-desktop etc.

P.S. Gnome itself is an environment which contains a lot of apps by default like mail client, browser etc. to let people get the system up and running with the most needed software. It's a complex solution by the way and it's not that bad. KDE has the same set of software. The other thing is that you may not like this or that application, so you are free to install your prefered one and associate it as the default. It's up to you to decide and it's all free. The thing is: you **should** google a bit and see what is removable and what's not.

Thanks, that worked quite nicely, it confirmed my own thoughts, but I didn't want to take the system down, so I thought I'd better ask. I also removed Pidgin (I gather it needs Evolution to work). I didn't have to uncheck the Evolution Alarm Notifier, it wasn't there.

I have no problem with Evolution being included in Ubuntu, I just think that it's pretty damned silly to have one specific email client tied so tightly into Gnome. What if I wanted to install Thunderbird and use it instead? I'm supposed to keep Evolution still installed? This doesn't make any sense at all!

In fact from a development point of view it sounds like what Microsoft does with Internet Exploder.

---

### Post by Gausian on 2009-05-15
the one thing that keeps me from uninstalling evolution is the calendar thats integrated with gnome.  i sync with my google calendar and can see appointments under the clock without having to log into google.

---

### Post by dcstar on 2009-05-15
> **themadhatter said:**
> Thanks, that worked quite nicely, it confirmed my own thoughts, but I didn't want to take the system down, so I thought I'd better ask. I also removed Pidgin (I gather it needs Evolution to work). I didn't have to uncheck the Evolution Alarm Notifier, it wasn't there.

I have no problem with Evolution being included in Ubuntu, I just think that it's pretty damned silly to have one specific email client tied so tightly into Gnome. What if I wanted to install Thunderbird and use it instead? I'm supposed to keep Evolution still installed? This doesn't make any sense at all!

In fact from a development point of view it sounds like what Microsoft does with Internet Exploder.

Rubbish, one component is "tied" into Gnome - the Calendar - and you can just leave that package while removing the rest.

Either that or you just install whatever e-mail client you like and simply change the default client to it - you are not forced to use anything.

---

### Post by TheExplorer on 2009-05-15
Yup. It's just a set of software to be up and running, even from a LiveCD, portably, anywhere you are and it's good. It's not like Microsoft. Even that Microsoft thing about their browser is rubbish. You are also free to install Firefox and make it default (the system will let you do it, notice it!). Other thing is that you should pay for M$, and this one is completely free and open-source. You are also free to get your teeth into its code, reprogram, compile without Evolution and use it :) Why not?
That's one of the main nerves of Linux philosophy.

P.S.
> I also removed Pidgin (I gather it needs Evolution to work).
Nope :) It never needed Evolution, it's a standalone package. You should learn more about Gnome otherwise you'll end up asking the same questions here forever with MS approach. Forget it :)

---

### Post by Wiebelhaus on 2009-05-15
> **themadhatter said:**
> I want to remove Evolution. I don't use it (100% webmail). And if I accidently click on an email address, it starts, slowing the system until I can kill it. 

Any good suggestions?

FYI, for those who will suggest that I should just kill the link, I've used Evolution before, and quite frankly hated it. Even if I wasn't using webmail I'd not want it on any computer I own.

Oh, and does anyone know why the hell it appears to be tied into the Gnome desktop? I can't think of any valid reason, and it appears to be a really dumb design choice.

This is how you fix the send to function to your web based email , check screenie.

---

### Post by jerrrys on 2009-05-15
i removed it once and much to my dismay, removed my desktop...now ill give it another try...thanks [TheExplorer....]("http://ubuntuforums.org/member.php?u=328690")

---

