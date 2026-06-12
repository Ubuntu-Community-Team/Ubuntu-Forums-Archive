---
title: "Will ubuntu keep including Gnome in future releases?"
date: 2011-09-12
forum: Desktop Environments
---

### Post by mw13068 on 2011-09-12
A while back (around the release of 11.04) I saw some rumors that Ubuntu would eventually discontinue Gnome support/inclusion in favor of Unity.

Can anyone tell me whether this rumor is true or not?  Is there an Ubuntu development plan/roadmap somewhere?

I've tried Unity, but I just don't like it.  Gnome is my preference.  If Ubuntu won't keep Gnome around then I'll have to switch to another distro.

---

### Post by ubudog on 2011-09-12
Correct - Gnome will not be included after 11.04.

However, you can add the Gnome PPA, and install Gnome like that, it just takes an extra 5 minutes after installing if you have a decent internet connection.

BTW: [Here]("https://launchpad.net/~gnome3-team/+archive/gnome3") is the PPA for Gnome 3.  I plan on creating a PPA for Gnome 2.32.0, for those of us who want to stay old school.

---

### Post by mw13068 on 2011-09-12
> **ubudog said:**
> Correct - Gnome will not be included after 11.04.

However, you can add the Gnome PPA, and install Gnome like that.

Thanks.  I'll probably just switch back to Debian stable.  I can't really get behind any distro that would trade a mature, clean, and easy-to-use desktop like Gnome for something like Unity.  If I wanted an iPad, I'd buy an iPad.


edit:

Oh lord,  I just looked at gnome3.org and they're headed down the same stupid ("we gotta make this look like a Mac") path... Perhaps Xubuntu is the way to go.

---

### Post by Frogs Hair on 2011-09-12
I don't know when this may be available for Ubuntu .[https://github.com/Perberos/Mate-Desktop-Environment](https://github.com/Perberos/Mate-Desktop-Environment)

Unity was / is an alternative to the Gnome 3 (shell). It is Gnome that is dropped support for Gnome 2.xx not Ubuntu . There is also a Gnome 3 fall-back mode that looks like Gnome 2 , but I don't know of this will be included in 11.10 or not .

---

### Post by ubudog on 2011-09-12
> **mw13068 said:**
> Perhaps Xubuntu is the way to go.
+1 on that.

---

### Post by saltmarshlamb on 2011-09-12
> **ubudog said:**
> +1 on that.

worked for me - mostly it's been an easy thing to deal with

---

### Post by MARP1961 on 2011-09-12
You will be able to install Gnome Shell through the Software Centre or Synaptic in version 11.10. The 'Gnome 2 Experience' in the future will limited to people using the XFCE desktop (like Xubuntu) or activating the Gnome Fallback in Gnome Shell by going to settings/graphics then selecting the 'Forced Fallback' to ON.

---

### Post by ubudog on 2011-09-12
> **saltmarshlamb said:**
> worked for me - mostly it's been an easy thing to deal with

Yep, it stays simple.  ;)

---

### Post by lkjoel on 2011-09-12
Ubuntu 11.10 will keep GNOME as an option (I don't know about future releases). It will have GNOME 3, but not GNOME 2.

---

### Post by bpitsolutions on 2011-09-12
Is there a way to strip Unity out of Ubuntu 11.04 or 11.10 and install  Gnome?  I understand the Ubuntu team is headed one direction but if KDE  is still on Kubuntu, would it be as simple as taking Kubuntu and  stripping out KDE and installing Gnome or taking Ubuntu and stripping  out Unity for Gnome?  Or as was pointed out earlier, just trying a new distro like Mint or Xbuntu?   I really dislike the Unity shell.  If we can't strip out Unity, maybe it is time to try Suse or Gentoo....

---

### Post by ubudog on 2011-09-12
I recommend just trying out Xubuntu for a while.

---

### Post by el_koraco on 2011-09-12
> **bpitsolutions said:**
> Is there a way to strip Unity out of Ubuntu 11.04 or 11.10 and install  Gnome?  I understand the Ubuntu team is headed one direction but if KDE  is still on Kubuntu, would it be as simple as taking Kubuntu and  stripping out KDE and installing Gnome or taking Ubuntu and stripping  out Unity for Gnome?  Or as was pointed out earlier, just trying a new distro like Mint or Xbuntu?   I really dislike the Unity shell.  If we can't strip out Unity, maybe it is time to try Suse or Gentoo....

Why strip stuff? Do a netinstall and apply only the stuff you want.

---

### Post by lkjoel on 2011-09-12
If you really want to strip unity, you can try this:
```
sudo apt-get purge `dpkg -l | awk '{print $2}' | grep "^unity.*"`

```

---

### Post by ubudog on 2011-09-12
> **lkjoel said:**
> If you really want to strip unity, you can try this:
```
sudo apt-get purge `dpkg -l | awk '{print $2}' | grep "^unity.*"`

```

Nice command.

Be sure to install another DM before doing that though.

---

### Post by lkjoel on 2011-09-12
Yeah, and don't go into Unity while you are running it!

---

### Post by mikodo on 2011-09-12
> **ubudog said:**
> I recommend just trying out Xubuntu for a while.
+1

I cut my computer teeth on Gnome 2, and was sad to think about having to go to Unity after EOL of Lucid. I installed Xubuntu on top of it and am really impressed! I never boot into Ubuntu with Gnome2 anymore. I still miss some of functionality of Nautilus, but with installing Xubuntu on top of Ubuntu, Nautilus is still there and Xfde can be tweaked to  use Nautilus and still have Xfde draw the desktop and use its menus. If you want to install Xubuntu alone, without having Ubuntu installed first, one and can still install nautilus and use it to mount devices and other services. That is what I missed in Xfce, the familiarity of mounting devs.

Xfce is much quicker than Gnome2, and with Xubuntu, I have remained in the 'buntu family and everything is still familiar to use like the repos, PPA's and updates.

Oh, what I did was burn a Live CD of it to see what is like first. You don't even have to do that to try it out temporarily first. You could just try it by:

```
sudo aptitude install xubuntu-desktop
```and choose it upon login. If you don't like it (I doubt you will), then you can un-install or use the CD for something else, with not much if anything to loose. Some regulars on this page, have been very helpful showing me the "ropes" so to speak; and I see them here still, helping.

I hope to see you here, too. :^)

---

### Post by Blasphemist on 2011-09-13
There are obvious issues with trying to stay with a DE no longer in development. And the people involved with that project are moving on for good reasons. I expect that much like when KDE 4 hit and was panned, many Gnome 2 users will find Gnome 3 their preference after all is said and done. Just as happened with KDE. 

But never fear, as has been pointed out there will be other Ubuntu flavors. Many as a matter of fact. Bodhi linux is one I think will come on strong, is as a matter of fact. Enlightenment E17 is very nice. It's extremely configurable, very lightweight and has a very modern feel. They have some great ideas such as click anywhere on any desktop for the menu and shelves. I think people will have even more choice that today going forward.

---

### Post by sarsbretta on 2011-09-16
> **ubudog said:**
> +1 on that.

+1

---

