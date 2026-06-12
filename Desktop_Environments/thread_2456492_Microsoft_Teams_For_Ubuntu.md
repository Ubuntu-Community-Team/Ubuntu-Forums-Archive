---
title: "Microsoft Teams For Ubuntu?"
date: 2021-01-12
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2021-01-12
Microsoft have released an official version of Teams for Linux. It is available as a .deb. There also seems to be an unofficial snap which uses something called Electron. I have used Teams on Windows how do these two versions stack up?
Has anyone used them? Is the Microsoft version of Teams likely to be available form the Ubuntu Repositories.

---

### Post by SeijiSensei on 2021-01-12
> **rsteinmetz70112 said:**
> Is the Microsoft version of Teams likely to be available form the Ubuntu Repositories.
Unless it's open-source, which seems unlikely, it won't be in the repositories.

---

### Post by ActionParsnip on 2021-01-12
[https://www.ubuntufree.com/download-microsoft-teams-for-ubuntu/](https://www.ubuntufree.com/download-microsoft-teams-for-ubuntu/)

---

### Post by ActionParsnip on 2021-01-12
Just install the deb and it'll install the application. If there are whinges about deps then run:
```

sudo apt-get -f install

```
and the deps will come down from the repos

---

### Post by rsteinmetz70112 on 2021-01-12
> **SeijiSensei said:**
> Unless it's open-source, which seems unlikely, it won't be in the repositories.

The repositories include proprietary drivers so I don't see any reason it couldn't be in the Universe repository, except Microsoft refusing permission.
Having it in the repositories would help insure the latest version was easily available.

---

### Post by rsteinmetz70112 on 2021-01-12
Has any one actually used either of the two currently available options? 

The snap says it currently not being developed since Microsoft released their own version then takes a swipe at the Microsoft version. 
From the github page:
> This project is in maintenance mode only. Microsoft is now providing a client that, more or less works.

---

### Post by deadflowr on 2021-01-12
The teams snap is official.
It's called teams and is published by Microsoft.

Edit: missed your post on that.


>  Is the Microsoft version of Teams likely to be available form the Ubuntu Repositories.
If Microsoft allows it to be. It would only be in Restricted or Canonical Partners though.
They may just keep it in their own repositories like Google does.
That allows them to control things like updating, among other things.

> Has any one actually used either of the two currently available options?
I haven't, as i have no need for it.

But you can test both for us and tell us how they perform and what issues ( what's missing; what does not work) they have.

---

### Post by grahammechanical on 2021-01-12
In Ubuntu 20.04 search the Software app for Microsoft and in the list there is Microsoft Teams - Preview. The Universe repository is enabled but not the Canonical Partners repository. This Teams Preview is a snap. The version is 1.3.00.30857 and the Details says that you need a commercial Office 365 subscription.

Installation of the deb app might be the preferred option. It depends on any licencing terms.

From the origin source.

[https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-is-now-available-on-linux/ba-p/1056267](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-is-now-available-on-linux/ba-p/1056267)

And for free!

[https://www.microsoft.com/en-gb/microsoft-teams/free?&OCID=AID2000628_SEM_0eAaOTGO&MarinID=0eAaOTGO%7C79645986309572%7Cmicrosoft%20teams%20free%7Cbe%7Cc%7C%7C1274334235465277%7Ckwd-79646055530279:loc-190&lnkd=Bing_Teams_Brand&msclkid=1f96ab7481c1154bb71bf69a18ff264b](https://www.microsoft.com/en-gb/microsoft-teams/free?&OCID=AID2000628_SEM_0eAaOTGO&MarinID=0eAaOTGO%7C79645986309572%7Cmicrosoft%20teams%20free%7Cbe%7Cc%7C%7C1274334235465277%7Ckwd-79646055530279:loc-190&lnkd=Bing_Teams_Brand&msclkid=1f96ab7481c1154bb71bf69a18ff264b)

Regards

---

### Post by rsteinmetz70112 on 2021-01-12
As far as I can tell at this time Microsoft is providing a .deb, but not a repository. 
I would prefer a repository I could rely on to stay updated. 
I have one app we use that is available through an OpenSUSE repository system which as I understand it allows developers to package multiple versions depending on type and version. 
It has worked well for me for a long time.

I'm going to load each on different machines and see how it works. I have two Ubuntu desktops at my house, for my wife and I to work from home at the same time.
I'm not sure how much opportunity I'll have to actually use them.

---

### Post by rsteinmetz70112 on 2021-01-12
> **grahammechanical said:**
>  This Teams Preview is a snap. The version is 1.3.00.30857 and the Details says that you need a commercial Office 365 subscription.s
[/QUOTE]

Thanks, that's weird. According to Microsoft Teams clients are available free for use (as in Beer) including the Linux client.

I was able to install the snap on one of my servers running 18.04 LTS earlier today. It just installed as usual.
I haven't had a chance to fire it up yet.
I haven't tried installing the .deb yet.

---

### Post by deadflowr on 2021-01-12
I see they've also created  flatpak version:
[https://flathub.org/apps/details/com.microsoft.Teams]("https://flathub.org/apps/details/com.microsoft.Teams")

---

### Post by rsteinmetz70112 on 2021-01-13
> **deadflowr said:**
> I see they've also created  flatpak version:
[https://flathub.org/apps/details/com.microsoft.Teams]("https://flathub.org/apps/details/com.microsoft.Teams")

That was mentioned earlier. I looked at it it seems to be the same version as the snap.
I've never used a flatpack and have little interest in adding yet another method of installing software to my computers. I'm still skeptical of snaps,

---

### Post by rsteinmetz70112 on 2021-01-18
FWIW, 

I've now installed Teams on three Ubuntu computers, one is a server that I haven't actually started Teams on yet. The other two are desktops with somewhat dated hardware I used the snap for one and downloaded the deb from the Microsoft website for the other. The Teams on the desktops seem to have fewer features than the version on my Windows desktop in my office. That may be because of the hardware. I understand Teams requires certain features in the CPU in order for some features like backgrounds to work. The Desktops are AMD Phenom II processors. The Server is a AMD FX and the Windows 10 Desktop is an AMD A-series with integrated GPU. It may also be that certain options are not turned on in Teams, although I couldn't find them in the Ubuntu desktop versions.

In order to really test it out I need to set up a meeting and see how they work. I'm also going to try my 1 year old Lenovo Ryzen Windows 10 laptop, it should have the latest features. I don't recall what kind of graphics hardware it has.

---

