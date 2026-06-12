---
title: "Just tried openSUSE KDE 11.2 - I want that look"
date: 2009-10-16
forum: Desktop Environments
---

### Post by MountainX on 2009-10-16
What would be involved to make Kubuntu look exactly like openSUSE 11.2 KDE? I want the same theme, same colors, same icons, same everything. Is there an easy way to do this?

Mainly I want to learn KDE. As much as I am impressed by openSUSE, for me to learn more about KDE, I can do it easier with Kubuntu given my lack of experience with YaST, Sax, etc. But I know I won't like Kubuntu unless I can make it look as elegant as openSUSE. (I installed Kubuntu a week ago and the look was just horrible in my opinion. Of course, I know others disagree, but that's my opinion.)

While I'm on the subject, the openSUSE installer kicks Ubuntu's butt. I was able to create an encrypted disk, create LVM groups and volumes inside that, format & install all from the graphical installer. In Ubuntu, this requires the alternate installer and the work flow is much more cumbersome (which makes a big difference in install time when the disk setup is complicated).

Ubuntu just needs to borrow this entire installer. ;) It is really good.

On my Thinkpad, everything just worked with openSUSE out of the box. With Kubuntu, much of my hardware did not work without extra setup (e.g., the Trackpoint, fingerprint scanner, etc.). However, I'll deal with those issues if I can just make Kubuntu look like openSUSE (green and all). :)

I'm still using Ubuntu on my main desktop, so don't kick me out of the community yet. [-X

---

### Post by Ekeluo on 2009-10-16
Can you upload or point to a screenshot for the look you want? I checked the website and the shots I saw leave me a bit confused.

Also, visit kde-look.org and use the integrated Get-Hot-New-Stuff portal to get new plasma themes, icon themes, colour schemes, etc.

---

### Post by Vermind on 2009-10-16
[openSUSE plasma theme]("http://www.kde-look.org/content/show.php/openSUSE?content=91434") on kde-look.org. Not sure this is what you want, but look though the kde-look site, you might find something you like.

---

### Post by MountainX on 2009-10-16
> **Ekeluo said:**
> Can you upload or point to a screenshot for the look you want?

I attached my screen shot. It is the stock KDE theme for openSUSE 11.2. It's the Oxygen theme with green colors.

---

### Post by MountainX on 2009-10-16
How would I just save the theme I'm using now (on openSUSE) and transfer it to Kubuntu? I know its a dumb question, but after 2 years of using Ubuntu, I never changed anything related to the theme or colors... nothing. I'm like a total newbie when it comes to themes. They have always been fine (until I tried Kubuntu!)

---

### Post by slakkie on 2009-10-16
> **MountainX said:**
> How would I just save the theme I'm using now (on openSUSE) and transfer it to Kubuntu? I know its a dumb question, but after 2 years of using Ubuntu, I never changed anything related to the theme or colors... nothing. I'm like a total newbie when it comes to themes. They have always been fine (until I tried Kubuntu!)

Just copy your $HOME/.kde* directories over and it should be there. Unless they have some theme stuff in /usr/share.. But then you copy over that stuff too :)

Although I don't have an issue with stock KDE of Ubuntu/Debian. I customize my own desktop so I have what I want/need.

---

### Post by MountainX on 2009-10-16
> **slakkie said:**
> Just copy your $HOME/.kde* directories over and it should be there. Unless they have some theme stuff in /usr/share.. But then you copy over that stuff too :)
.

Thanks. I do see kde stuff in /usr/share. I also see kde and kde4 folder under my home directory. It seems like there is kde config stuff in a lot of different places. Not sure how to make sure I find it all.

---

### Post by slakkie on 2009-10-16
Your personal preferences are stored in .kde directories. .kde4 was only present when you already had a .kde dir which belonged to kde3.

I have .kde as a symlink to .kde4, and when I use hardy I simple remove the link and relink it to .kde3. 

Anyhowz, it could be that some stuff from your current fedora theme is stored in /usr/share you will need to copy over those file to your Ubuntu machine, or to your own .kde dir.

For example, all the default themes of ubuntu are installed here: 

/usr/share/kde4/apps/desktopthemev

I think it is safe to copy them to $HOME/.kde/share/apps/desktoptheme. Make a backup first of your .kde dir!

(assuming .kde is your .kde4 dir ;)).

```

tar zcvf dot_kde.tgz .kde
cp -r /usr/share/kde4/apps/desktoptheme/*  $HOME/.kde/share/apps/desktoptheme/

```

---

### Post by Dullstar on 2009-10-16
That was what I thought when I saw the Gentoo screenshots on Wikipedia!

---

### Post by Rifester on 2009-11-23
[B]Did you ever succeed in getting the SUSE look in Kubuntu?  
[/B]

---

### Post by MountainX on 2009-11-23
> **MRife said:**
> [B]Did you ever succeed in getting the SUSE look in Kubuntu?  
[/B]

There were far too many disappointing things in Kubuntu. So I ended up going back to openSUSE 11.2. Even as a release candidate, it is more stable and more polished than the final release of Kubuntu Karmic (at least on my Thinkpad). 

I do not really like Novell and I'm not such a big fan of RPMs. I want to be using Kubuntu, but openSUSE is just too good. I'm actually loving it. :D

---

### Post by Rifester on 2009-11-24
What Thinkpad are you using (did you have any hardware problems after install)?   I really liked 11.2 but my video card does not like it (it worked great on the live cd).  I have been testing Kubuntu the last few weeks...

---

### Post by MountainX on 2009-11-24
> **MRife said:**
> What Thinkpad are you using (did you have any hardware problems after install)?
T61p 
No problems. Zero. None. :D

---

