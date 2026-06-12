---
title: "ubuntu or kde + kubuntu?"
date: 2005-08-29
forum: Desktop Environments
---

### Post by beewer on 2005-08-29
Hi everyone.

I'm planning to switch to Ubuntu or Kubuntu from Mandriva because I'm "bit" frustrated on rpm. Apt-get system seems much more convenient. 

One very important reason is also that I don't want to upgrade my OS from cdrom. I have found this bit unstable and risky and I really don't like to do fresh install every year or so.

But to the question: I prefer KDE over gnome. Which should I choose Kubuntu or Ubuntu? 

Kubuntu seems like obvious choice but since it is branch of Ubuntu I'm bit afraid that it will be bit behind Ubuntu in security updates etc. 

So how Kubuntu and Ubuntu differ? Do they have same repositories? 
Do guides at [http://ubuntuguide.org/](http://ubuntuguide.org/) apply also to Kubuntu?

If I install KDE to Ubuntu with command:
sudo apt-get install kubuntu-desktop

Do I get same packages as I would get with Kubuntu? And KDE packages from Ubuntu and Kubuntu updated in simultaniously or does Ubuntu get them slower?


-B

---

### Post by snpz on 2005-08-29
I installed ubuntu, but i prefer KDE.
I just installed KDE with apt-get. I think that repositories are the same for both - kde and gnome. if u install ubuntu then default xwindow manager will be gnome, but if kubuntu, then KDE. That's it.

---

### Post by incinerator on 2005-08-29
[http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html) is a kubuntified version of ubuntuguide.org
Also, read the FAQ at [http://kubuntu.org/](http://kubuntu.org/) to find out what's different and what not.

Why don't you download the ubuntu and kubuntu livecds to see for yourself?

I don't understand your fear of Kubuntu being more unstable and insecure than Ubuntu. Kubuntu is integral part of ubuntu in all but name, they use the same package repositories and therefore everything but the kde specific desktop environment software is the same: same kernel, same device drivers, same base system, same X server, same security updates. How could it possibly be more insecure, then?

I did install kubuntu from the kubuntu dvd. I had no big problems during installation, only one small quirk I could resolve in a matter of seconds. If you install ubuntu first and then use apt-get to install the kubuntu desktop you will have to do some work getting kdm to work, getting rid of esd etc. Also, it will leave lots of unnecessary gnome software occupying precious space on your hard disk. Why not install Kubuntu using a Kubuntu cd, then?

---

### Post by beewer on 2005-08-29
[QUOTE=incinerator]
I don't understand your fear of Kubuntu being more unstable and insecure than Ubuntu. Kubuntu is integral part of ubuntu in all but name, they use the same package repositories and therefore everything but the kde specific desktop environment software is the same: same kernel, same device drivers, same base system, same X server, same security updates. How could it possibly be more insecure, then?
[/QUOTE]

Thanks for replies for both of you. Maybe I didn't explain myself very well. I was concerned that if Kubuntu would get security updates later than Ubuntu because I didn't know they use same repositories.

And another thing, as Ubuntu seems to be "main" version I am worried that if Kubuntu is not as polished as Ubuntu and does not get same level of support. 

But yeah, maybe I need a cup of RTFM  :smile:

---

### Post by AndyAWS on 2005-08-29
No need to worry there, the support is beautiful for both distros. They use the same core programs, the only real difference is which desktop gets completely setup, and you can easily add gnome to Kubuntu or KDE to Ubuntu later.

In fact for Kubuntu (or Ubuntu with Kubuntu-desktop installed) there are extra repos for KDE3.4.1 and 3.4.2. You can find them easily in the Kubuntu forum.

Personnaly I use Ubuntu with Kubuntu-desktop package installed, but I don't see any advantage to either other than personal preference.

If KDE is your thing, then go with Kubuntu...If you decide later that you need some gnome things you can later install the Ubuntu-desktop package.

---

### Post by incinerator on 2005-08-29
Well, kubuntu started off a wee bit later than ubuntu, you mave have a point here. Some parts of the kubuntu kde desktop are not as polished as the Ubuntu Gnome desktop may be. However, kubuntus kde certainly is not worse than any other GNU/Linux distro's kde.

As I said before, just download the LiveCDs and check before you commit your hard disks.

---

### Post by beewer on 2005-08-29
Thanks for information. Could someone please answer to one more question:
If I install Ubuntu and use apt-get install kubuntu-desktop to install kubuntu-desktop will I be able to choose between KDE and gnome from login screen? 

I think that optimal solution for me would be chance to choose between gnome/KDE per session.

-B

---

### Post by Hobbsee on 2005-08-29
[QUOTE=beewer]Thanks for information. Could someone please answer to one more question:
If I install Ubuntu and use apt-get install kubuntu-desktop to install kubuntu-desktop will I be able to choose between KDE and gnome from login screen? 

I think that optimal solution for me would be chance to choose between gnome/KDE per session.

-B[/QUOTE]
 Yes, you just click session, and select whether you want to use kde or gnome for each session.

---

### Post by beewer on 2005-08-29
[QUOTE=incinerator] have to do some work getting kdm to work, getting rid of esd etc. Also, it will leave lots of unnecessary gnome software occupying precious space on your hard disk. [/QUOTE]

Hmm, about this esd. If I don't get rid of it does this mean that sound does not work in KDE? Or that simultanious sounds do not work? Which sound system Kubuntu uses by default?

I'm bit confused about these different sound systems in linux. Imho they are bit messy in all distros.

I think that RPM and sounds are two biggest problems in linux for me at least atm. I hope that no one takes this as a troll  :)

---

### Post by masteryoda on 2005-08-29
Hi beewer,
                I am a linux newbie... so before I got into Linux I too had the same questions.. infact a lot more questions than this. 
1) Ubuntu and Kubuntu are very much the same... except for the Gnome and KDE.
U can anytime change from one to other....
apt-get install kubuntu-desktop (Ubuntu to Kubuntu)
apt-get install Ubuntu-desktop (Kubuntu to Ubuntu)
2) Both of them have the same product cycle... versions will be same and upgraded at the same time. (also the cycle is fixed... thats the advantage over other distros)
3) As both have the same core... all the Ubuntu tips and tricks, softwares etc...etc... works perfectly with Kubuntu... Infact I have configured my Kubuntu from [www.ubuntuguide.org](www.ubuntuguide.org)
4) If u upgrade from one to other... you end up loosing abt 300-500MB of extra  space..so if you are sure that u want KDE... go for Kubuntu.. why to waste resources?

Finally answer to your last question... yes.. if u install kubuntu over Ubuntu... or even if you install Ubuntu over Kubuntu... you can choose the session type at login screen.

---

### Post by incinerator on 2005-08-29
[QUOTE=beewer]Hmm, about this esd. If I don't get rid of it does this mean that sound does not work in KDE? Or that simultanious sounds do not work? Which sound system Kubuntu uses by default?

I'm bit confused about these different sound systems in linux. Imho they are bit messy in all distros.

I think that RPM and sounds are two biggest problems in linux for me at least atm. I hope that no one takes this as a troll  :)[/QUOTE]

Sound DOES work in kde, so does simultaneous playback of multiple sounds. If you have installed both kde and gnome you may need to do some extra configuration work to make their sound systems peacefully coexist. I wouldn't really know, I don't use gnome.

---

### Post by beewer on 2005-08-29
Thanks everyone  for answers. I will try Kubuntu.  \\:D/

---

