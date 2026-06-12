---
title: "[SOLVED] Fedora 9"
date: 2008-05-08
forum: Fedora/RedHat and derivatives
---

### Post by NikS on 2008-05-08
Hey whens Fedora 9 releasing??

I heard rumors that it was to be out by 24th of previous month, but...

Is It??

---

### Post by Antman on 2008-05-08
No, it was delayed. Check out [www.fedoraproject.org ]("http://fedoraproject.org/")for the current release date.

---

### Post by justin whitaker on 2008-05-08
They decided to give Pulse Audio a bit more time in the oven, among other things....not a bad idea really. Other projects could learn from that...:)

---

### Post by igknighted on 2008-05-10
> **justin whitaker said:**
> They decided to give Pulse Audio a bit more time in the oven, among other things....not a bad idea really. Other projects could learn from that...:)

PA has been (rather seamlessly) integrated since Fedora 8, so I doubt that's it.  I think (although I could be wrong) that packagekit is one of the primary culprits.

---

### Post by pelle.k on 2008-05-10
Too bad the official nvidia driver doesn't work with F9 yet, as i'm alright with running the "libre" nv driver, but what good is that when i can't suspend my computer? Other that that, F9 looks really sweet. I'm *so* glad they did change the "login sound" from that awful "beep" to the musical score instead.
I would like to change the GDM background though.

---

### Post by karellen on 2008-05-11
day after tomorrow, 13 of may. anybody else anxious? :popcorn:

---

### Post by Antman on 2008-05-11
> **karellen said:**
> day after tomorrow, 13 of may. anybody else anxious? :popcorn:
Not really, I'm already running Rawhide on one of my computers:KS

---

### Post by karellen on 2008-05-11
> **Antman said:**
> Not really, I'm already running Rawhide on one of my computers:KS

and how's like?

---

### Post by pelle.k on 2008-05-11
Hehe, i almost summed it up in my previous post. Well, maybe not.
It's fast, and i would say it's an improvement over F8 overall. This must be the buggiest **gnome** (gnome 2.22) release in a long time, so kudos to the fedora developers for stabilizing it. The new gdm (fedora is the only big time distro to ship 2.22) is lacking some mechanism to change it's appearance as of now though.
The new sound theme is nice. Not too much, just enough in my oppinion.
You still have to install custom packages to get nice LCD font rendering though. :(
However, i see no reason to switch until there's an nvidia driver available in the livna repos (speaking for myself, or course).

---

### Post by Istonian on 2008-05-11
I will try out F9, but I don't think it will replace Ubuntu. I really like packagekit. I used it with Foresight, but Foresight does not use packagekit well at all.

---

### Post by igknighted on 2008-05-11
> **pelle.k said:**
> Hehe, i almost summed it up in my previous post. Well, maybe not.
It's fast, and i would say it's an improvement over F8 overall. This must be the buggiest **gnome** (gnome 2.22) release in a long time, so kudos to the fedora developers for stabilizing it. The new gdm (fedora is the only big time distro to ship 2.22) is lacking some mechanism to change it's appearance as of now though.
The new sound theme is nice. Not too much, just enough in my oppinion.
You still have to install custom packages to get nice LCD font rendering though. :(
However, i see no reason to switch until there's an nvidia driver available in the livna repos (speaking for myself, or course).

Is it (nvidia) available via freshRPMs and DKMS yet?  Plus, livna usually finalizes the nvidia driver right at release, so when it goes public Livna should have the nvidia driver, and if not very shortly thereafter.  They only do every 4th kernel until release IIRC.

---

### Post by pelle.k on 2008-05-12
> Is it (nvidia) available via freshRPMs and DKMS yet?
I doesn't seem like there are. There *are* nvidia drivers in livna, but they just doesn't work, yet.
From what i understand, at first there was a problem with kernel 2.6.25 and nvidia, but i think that was fixed upstream. The second problem is with xorg server 1.5 and the proprietary nvidia driver. So, as of now you have to downgrade X to the version from F8 to get it working :(
It'll probably get fixed soon enough, but probably not in time for the F9 release. After all, as far as fedora is concerned, this isn't their problem really.

---

### Post by mthei on 2008-05-13
I'm grabbing the LiveCD right now, and maybe try to upgrade with it next week or so, as I've read it's the only way for a relatively safe upgrade. If not, I may give Hardy a try (there are a small number of conveniences that I miss from Ubuntu, or any Debian-based distro), but Fedora8 has served me nicely for the last five months. Along with Ubuntu and Sidux, Fedora is one of the nicest installers I've used.

---

### Post by igknighted on 2008-05-13
> **pelle.k said:**
> I doesn't seem like there are. There *are* nvidia drivers in livna, but they just doesn't work, yet.
From what i understand, at first there was a problem with kernel 2.6.25 and nvidia, but i think that was fixed upstream. The second problem is with xorg server 1.5 and the proprietary nvidia driver. So, as of now you have to downgrade X to the version from F8 to get it working :(
It'll probably get fixed soon enough, but probably not in time for the F9 release. After all, as far as fedora is concerned, this isn't their problem really.

True... Fedora would never hold a release up for a proprietary driver.  Hopefully it will be fixed soon.  Might be a good chance to try noveau at least haha, as I know that NV doesn't work with my card.  And I simply can't live with VESA.

---

### Post by agim on 2008-05-13
torrenting Fedora 9 now. I am looking forward to using it.

---

### Post by VirtuAlex on 2008-05-14
> **igknighted said:**
> True... Fedora would never hold a release up for a proprietary driver.  Hopefully it will be fixed soon.  Might be a good chance to try noveau at least haha, as I know that NV doesn't work with my card.  And I simply can't live with VESA.

I've got nouveau working with dual head today under Fedora 9. No compiz for now, but at least I can work normally.

---

### Post by igknighted on 2008-05-15
> **pelle.k said:**
> I doesn't seem like there are. There *are* nvidia drivers in livna, but they just doesn't work, yet.
From what i understand, at first there was a problem with kernel 2.6.25 and nvidia, but i think that was fixed upstream. The second problem is with xorg server 1.5 and the proprietary nvidia driver. So, as of now you have to downgrade X to the version from F8 to get it working :(
It'll probably get fixed soon enough, but probably not in time for the F9 release. After all, as far as fedora is concerned, this isn't their problem really.

It's there now (new beta driver from nvidia).  Not in Livna yet though, so make sure you have DKMS installed.  It's a better method than kernel modules anyways, in case the livna maintainers don't have the module built right away (plus you can spin your own kernel and still use the driver from the repo's).

---

