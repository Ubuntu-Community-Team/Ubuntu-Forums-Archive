---
title: "Wireless on Fedora 8"
date: 2007-11-13
forum: Fedora/RedHat and derivatives
---

### Post by steveneddy on 2007-11-13
I have a laptop that I have installed Fedora 8 on and I can't seem to get the wireless going. Ethernet won't connect either, BTW.

What can I be doing wrong?

---

### Post by Vitamin-Carrot on 2007-11-13
BWAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA

One of the many reasons why i went from fedora to Ubuntu.

---

### Post by igknighted on 2007-11-13
> **steveneddy said:**
> I have a laptop that I have installed Fedora 8 on and I can't seem to get the wireless going. Ethernet won't connect either, BTW.

What can I be doing wrong?

Well, Fedora is a Free Software only distribution, so out of the box it has none of the proprietary bits (like certain wifi drivers) that Ubuntu has.  Fedora is like Debian in this sense.  Don't worry, however, the drivers are all available easily.  We need to know more information about what type of wireless card you have.

Can you run the command lspci and report the results?  You may need to be root to run this command, i forget if it is in the $path of a normal user in fedora.  Anyhow, once you post the output of that command, we can point you to the drivers or firmware you need.

Another question... does your wifi (and ethernet) work in Ubuntu?  If so, how did you set it up, and did you try doing it the same way in Fedora?

---

### Post by bapoumba on 2007-11-13
> **Vitamin-Carrot said:**
> BWAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA

One of the many reasons why i went from fedora to Ubuntu.

@ Vitamin-Carrot: this is useless. please consider not posting if you do not wish to help, thanks.

---

### Post by steveneddy on 2007-11-13
> **Vitamin-Carrot said:**
> BWAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA

One of the many reasons why i went from fedora to Ubuntu.

That is funny. I am not offended. Do not concider writing him up for this.

I have aSystem76 driver for this thing. think O should use that?

---

### Post by igknighted on 2007-11-13
> **steveneddy said:**
> That is funny. I am not offended. Do not concider writing him up for this.

I have aSystem76 driver for this thing. think O should use that?

No, all the drivers you could need are available in the fedora repo's (well, third party ones like Livna at least) if you know which ones they are

---

### Post by bapoumba on 2007-11-13
> **steveneddy said:**
> That is funny. I am not offended. Do not concider writing him up for this.
No I have not. I just posted in the thread, thanks :KS

---

### Post by steveneddy on 2007-11-13
> **igknighted said:**
> Well, Fedora is a Free Software only distribution, so out of the box it has none of the proprietary bits (like certain wifi drivers) that Ubuntu has.  Fedora is like Debian in this sense.  Don't worry, however, the drivers are all available easily.  We need to know more information about what type of wireless card you have.

Can you run the command lspci and report the results?  You may need to be root to run this command, i forget if it is in the $path of a normal user in fedora.  Anyhow, once you post the output of that command, we can point you to the drivers or firmware you need.

Another question... does your wifi (and ethernet) work in Ubuntu?  If so, how did you set it up, and did you try doing it the same way in Fedora?

Wireless and Ethernet work well in Ubuntu, I just wanna try out Fedora.

Here is the wifi stuff

```

Intel Corporation PRO/Wireless 3945ABG Network Connection

```

I guess I just need to do a little more tweaking.

If I could at least get Ethernet going, I could work on the wireless later.

---

### Post by insanedc on 2007-11-13
I had to install Network Manager from the repositories. Then, I was able to use wireless just like Ubuntu. 

I don't know why this extra step is necessary, as the Live CD just works with wireless (at least it did for me).

---

### Post by steveneddy on 2007-11-13
> **insanedc said:**
> I had to install Network Manager from the repositories. Then, I was able to use wireless just like Ubuntu. 

I don't know why this extra step is necessary, as the Live CD just works with wireless (at least it did for me).

I can't get on the internet - is htis on the 4 gig DVD I had to burn?

Hope so. I'm on my way home from work - I'll look when I get there.

---

### Post by Antman on 2007-11-13
> **steveneddy said:**
> I can't get on the internet - is htis on the 4 gig DVD I had to burn?

Hope so. I'm on my way home from work - I'll look when I get there.

Yeah, I have the same wifi card and the Fedora DVD worked fine, BUT for some reason Fedora has the NetworkManager services disabled by default. So before I could get my 3945 to work I had to enable the two NeworkManager services that are listed. I believe the "Sevices" menu is listed under "Administration."

---

### Post by igknighted on 2007-11-13
> **Antman said:**
> Yeah, I have the same wifi card and the Fedora DVD worked fine, BUT for some reason Fedora has the NetworkManager services disabled by default. So before I could get my 3945 to work I had to enable the two NeworkManager services that are listed. I believe the "Sevices" menu is listed under "Administration."

Yeah, i second this as the cause.  NM is not enabled on the DVD install by default.  Here's a blurb from the fedora-devel mailing list explaining why: 
[QUOTE=fedora-devel]> Please make it on by default also for DVD install images.

Till it works for all the systems Fedora targets (including those with
no permanent GUI session that also need network/wifi connexion) the
answer is no.

Right now NetworkManager is targetting a very small user niche, so
it's only usable as default in the spin dedicated to this niche (and
one could argue the spin desktop target audience is wider than the
laptop-only no-daemon dumbed-down desktop NetworkManager supports)[/QUOTE]

It is a fairly simple one click procedure to enable it, and most desktop users are recommended to use the liveCDs, as they are spins that are tailored to the desktop, while the DVD is meant as a generic install and as such has no such tailorings.  I guess I understand their reasoning behind this, as for gui-less systems, a networking procedure reliant on nm-applet is a bit of a pain ;).

Note that the firmware for that device is on the DVD media, i confirmed that yesterday while doing an install.  You may or may not have installed it during your install, so insert the DVD and try to install it via yum if you have further issues.

---

### Post by steveneddy on 2007-11-14
I think I'm gonna play with this through the Thanksgiving holidays, but I think I may like to try OpenSuse also. 

This is reallya royal PITA, IMHO.

They should really make this easier in this day and age.

---

### Post by igknighted on 2007-11-14
> **steveneddy said:**
> I think I'm gonna play with this through the Thanksgiving holidays, but I think I may like to try OpenSuse also. 

This is reallya royal PITA, IMHO.

They should really make this easier in this day and age.

It's not hard, its different.  I've done the wireless setup in Fedora (even on the DVD install) quite a few times already with Fedora 8.  It works perfectly.

You are assuming (incorrectly) that the DVD you installed from was tailored for desktop use (like the live spins are, and like Ubuntu is).  It is not.  It is a rather generic start so those who are creating a webserver, and those doing clustering, and those installing a desktop OS and others can all have the same disk, and customize the services and such to their liking.  If you want a distro that is already setup with defaults that work well for desktop users, try one of the many desktop-specific spins.  But your criticism here is aimed poorly.

---

### Post by steveneddy on 2007-11-14
> **igknighted said:**
> It's not hard, its different.  I've done the wireless setup in Fedora (even on the DVD install) quite a few times already with Fedora 8.  It works perfectly.

You are assuming (incorrectly) that the DVD you installed from was tailored for desktop use (like the live spins are, and like Ubuntu is).  It is not.  It is a rather generic start so those who are creating a webserver, and those doing clustering, and those installing a desktop OS and others can all have the same disk, and customize the services and such to their liking.  If you want a distro that is already setup with defaults that work well for desktop users, try one of the many desktop-specific spins.  But your criticism here is aimed poorly.

My criticism here was the fact that I thought that this distro release is a Pain In The A S S . (sorry, family people)

I was actually expecting something different and my thread is to discover answers. 

I'm not opposed to setting up Linux, I would like to have a desktop and wireless working out of the box or answers that are easier to find than the ones that I haven't found on the Fedora website.

I posted here because I know that there is a strong Fedora/RedHat community nestled in the Ubuntu Forums.

I am allowed to criticize an OS, especially if it is my thread.

It is frustrating, but I just would like to know, at this point, how to get GDM working at boot, wireless working at log in and a working desktop system, in 64 bit, so I can test to see if this distro is a direction that I can go for my professional computing needs.

At the moment, my professional needs require that I have a working, GUI desktop.

Easy.

---

### Post by igknighted on 2007-11-14
> **steveneddy said:**
> My criticism here was the fact that I thought that this distro release is a Pain In The A S S . (sorry, family people)

I was actually expecting something different and my thread is to discover answers. 

I'm not opposed to setting up Linux, I would like to have a desktop and wireless working out of the box or answers that are easier to find than the ones that I haven't found on the Fedora website.

I posted here because I know that there is a strong Fedora/RedHat community nestled in the Ubuntu Forums.

I am allowed to criticize an OS, especially if it is my thread.

It is frustrating, but I just would like to know, at this point, how to get GDM working at boot, wireless working at log in and a working desktop system, in 64 bit, so I can test to see if this distro is a direction that I can go for my professional computing needs.

At the moment, my professional needs require that I have a working, GUI desktop.

Easy.

Fedora has a version for this, but you did not use it.  There is a gnome and a KDE "spin", which are live CDs that are custom configured to be ready to go desktop systems.  The DVD is in many ways similar to doing a base install of Ubuntu from the server CD and adding the packages yourself.  See here: [http://fedoraproject.org/get-fedora](http://fedoraproject.org/get-fedora) (note at the bottom there is a link for more custom spins, where you will find a gaming spin, a developer's spin and much more).  These are all official project releases and use the same repo's, they are just configured for different purposes by default.  The gnome and KDE live media are the ones that will suit your purposes best in this case.

I'm sorry, I was a bit harsh sounding with the previous post.  I was simply pointing out that Fedora can indeed do exactly what you want, you simply picked the wrong media, in case you wanted to try using that instead to see if it is more what you were looking for.

---

### Post by steveneddy on 2007-11-15
I DLed the Fedora Live CD last night and I will try that, but I would like an installed version of the 64 bit system.

I also DLed the OpenSuse to try that out also.

I'm gonna hammer out the issues with this Fedora before I give it up.

---

### Post by igknighted on 2007-11-15
> **steveneddy said:**
> I DLed the Fedora Live CD last night and I will try that, but I would like an installed version of the 64 bit system.

Whats wrong with this disk (edit: or the equivalent KDE one)?  It should do all that better than the 4gb DVD does.

[http://download.fedoraproject.org/pub/fedora/linux/releases/8/Live/x86_64/Fedora-8-Live-x86_64.iso](http://download.fedoraproject.org/pub/fedora/linux/releases/8/Live/x86_64/Fedora-8-Live-x86_64.iso)

---

### Post by steveneddy on 2007-11-15
> **igknighted said:**
> Whats wrong with this disk (edit: or the equivalent KDE one)?  It should do all that better than the 4gb DVD does.

[http://download.fedoraproject.org/pub/fedora/linux/releases/8/Live/x86_64/Fedora-8-Live-x86_64.iso](http://download.fedoraproject.org/pub/fedora/linux/releases/8/Live/x86_64/Fedora-8-Live-x86_64.iso)

Yeah - that's the one I DLed last night.

I'm gonna try and give it a try tonight.

---

### Post by igknighted on 2007-11-15
> **steveneddy said:**
> Yeah - that's the one I DLed last night.

I'm gonna try and give it a try tonight.

Ahh.  I think you will find this to be a much better solution.

---

### Post by RebounD11 on 2007-11-17
I had to uninstall Network Manager to get any networking...

:| the old one was working fine... they could at least keep it in the repos :D

---

### Post by steveneddy on 2007-11-18
I DLed the OpenSUSE DVD and the Fedora 8 DVD this weekend and fought them until I finally gave up. I have OpenSUSE installed, but I think I'm gonna put something else in it's place.

The battle just to get wireless, bluetooth and a simple GUI desktop is ultimately frustrating. The small problems I had with Ubuntu in the beginning were nothing compared to the nightmare of Fedora 8 and OpenSUSE 10.3.

Don't get me wrong. These two free OS's are at the top of the game. Very smooth and very nice looking. There is very little documentation on the web, or it is hard to find, unlike Ubuntu. 

Thanks you, Ubuntu developers. I didn't realize how good we had it over here in Ubuntu land.

---

### Post by RebounD11 on 2007-11-20
OpenSuSE worked great for me. Best Distro ever at hardware detection. Fedora too (I just had to fight with the network manager - btw I have an Ovislink Airlive 2000PCI wireless card and it detected it perfectly which is very rare, so far Sabayon, OpenSuSE 10.3 and Fedora 8 only got it right so far). 

My wireless was the reason I quit Ubuntu, I got it to work in about 2 weeks with tons of help from the this forum, and I had to make a nasty compromise:
either have only wireless, or only have wired network (and no way I could get my wireless card in monitor mode). 

So I guess one man's trash is another man's treasure :D

---

### Post by steveneddy on 2007-11-20
> **RebounD11 said:**
> OpenSuSE worked great for me. Best Distro ever at hardware detection. Fedora too (I just had to fight with the network manager - btw I have an Ovislink Airlive 2000PCI wireless card and it detected it perfectly which is very rare, so far Sabayon, OpenSuSE 10.3 and Fedora 8 only got it right so far). 

My wireless was the reason I quit Ubuntu, I got it to work in about 2 weeks with tons of help from the this forum, and I had to make a nasty compromise:
either have only wireless, or only have wired network (and no way I could get my wireless card in monitor mode). 

So I guess one man's trash is another man's treasure :D

Yeah - I thought that strange also that I couldn't get wireless working on Fedora 8 and got it to work on OpenSUSE before I got tired of the hassle and reformatted the HD and kept Ubuntu. I think that liked Fedora better, though, just wish that the DVD I installed from (64 bit) was better at starting up a GDM session and detecting wireless.

This is 2007, almost 2008, and the two biggest names in Linux can't get as much going on first boot as Ubuntu can.

Ubuntu still has my business and will for some time to come.

But I still may try Fedora in the future, maybe.

---

### Post by igknighted on 2007-11-20
> **steveneddy said:**
> Yeah - I thought that strange also that I couldn't get wireless working on Fedora 8 and got it to work on OpenSUSE before I got tired of the hassle and reformatted the HD and kept Ubuntu. I think that liked Fedora better, though, just wish that the DVD I installed from (64 bit) was better at starting up a GDM session and detecting wireless.

This is 2007, almost 2008, and the two biggest names in Linux can't get as much going on first boot as Ubuntu can.

Ubuntu still has my business and will for some time to come.

But I still may try Fedora in the future, maybe.

Not to beat a dead horse, but those two can never support as much out of the box.  Ubuntu includes Atheros drivers and non-free firmware, while OpenSuse and Fedora (for free software reasons) wont go near that stuff with a 10ft pole.  So while yes, you are absolutely correct about Suse and Fedora not working OOTB on as much hardware, it is a philosophic choice.

And how are suse and fedora the biggest names in linux?  Ubuntu is the biggest name in linux hands down, followed by red hat.  I would call suse third, and fedora a rather distant 4th.  *note* this is my understanding of the outside world's view of linux, not the linux community itself.

---

### Post by RebounD11 on 2007-11-21
> **igknighted said:**
> And how are suse and fedora the biggest names in linux?  Ubuntu is the biggest name in linux hands down, followed by red hat.  I would call suse third, and fedora a rather distant 4th.  *note* this is my understanding of the outside world's view of linux, not the linux community itself.

I would say RedHat and Fedora go kind of together like SuSE and OpenSuSE. At least this is how I see things :)

---

### Post by steveneddy on 2007-11-23
What I really meant by that was that OpenSuse/SUSE and Fedora/Red Hat are the most popular in the "professional" world. They are the versions that are developed more heavily for professional and industrial applications than any other. 

Not that Ubuntu or any other isn't up to the task, but there aren't many companies in the professional world that would allow you to use a "free" OS as opposed to Red Hat or SUSE.

AAMOF - I understand that the only version of Linux that can be used while working on sensitive Gov't apps is Red Hat. 

Also in sensitive Gov't stuff that the Windows machines aren't allowed to access any type of network outside of a local LAN. No internet. Period.

I'm gonna try Fedora again in the future. Just not right away. I know I will need the .rpm and Red Hat skills soon. Maybe after the holidays. I just expected more out of Fedora than I got.

---

