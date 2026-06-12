---
title: "x1900 questions"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by Exuus on 2007-07-24
I've been using Ubuntu for roughly a week now and I still haven't managed to get compiz working. I've followed at least ten different guides posted both here and elsewhere online, all to no avail.

Should I just wait until the next set of ATI drivers are released that may hopefully make the whole process a lot easier or just accept that I can't ever have nice things? :)

Is there any guide that I'm missing that will go through everything step by step for setting up ubuntu and compiz on an x1900 in particular?

Apart from this, everything seems to work well and I'm very impressed with my first few days of using Ubuntu.

Thanks for any available help

---

### Post by amadeus266 on 2007-07-25
ATI's driver is still sketchy at best. Search the forums for ENVY. Can't promise it will work but it can't hurt.

---

### Post by Exuus on 2007-07-25
So is envy another set of drivers? I've only heard of the ATi drivers (which don't support using compiz or Beryl) and the third party drivers (which support beryl/compiz but not my graphics card).

---

### Post by Espreon on 2007-07-25
No,no,no,no Envy is a script that builds the drivers from source and automagically configures your xorg.conf to use the driver properly and it handles all dependencies in order for the card/driver to work properly.

Link to the Envy .deb: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb)

Eventhough I can get fglrx to work w/o Envy, for some reason on my latest Feisty reinstall fglrx would only work with XGL if fglrx was setup with Envy.

---

### Post by Exuus on 2007-07-25
Forgive me for asking a very obvious question, but how do I use that link?

Do I add it to repositories in synaptic or is it something else I'm missing? Also, does that set up everything, or do I still have to mess about with sessions, or can I just then install compiz?

---

### Post by Espreon on 2007-07-25
If you are using Firefox (I use Swiftfox, but won't be a difference). Click the link and hit the open option (Open with GDebi Installer) to install it, if that ain't working just download it (it is a file) and install it.

---

### Post by Espreon on 2007-07-26
> **thanos12 said:**
> i dont know how to help u man:(
[IMG]http://s4.bitefight.gr/c.php?uid=15792[/IMG]

If thats all you are gonna say, w/o contributing anything to help then you might as well not post at all!

Also BUMP.

---

### Post by Apocrypha on 2007-07-26
I have it working on my X1950 Pro by following instruction here. I used this [guide]("http://ubuntuforums.org/showthread.php?t=482773") specifically, but you've probably already seen it.

What I'm saying is it's possible (I didn't think it would be on the X1950 because it isn't listed in the fglrx capabilities).

---

### Post by jcostom on 2007-07-26
> **Apocrypha said:**
> I have it working on my X1950 Pro by following instruction here. I used this [guide]("http://ubuntuforums.org/showthread.php?t=482773") specifically, but you've probably already seen it.

What I'm saying is it's possible (I didn't think it would be on the X1950 because it isn't listed in the fglrx capabilities).

That guide is very useful.  It (mostly) mimics what I did to get an x1950 running with Xgl and compiz-fusion.

Despite not being shown on the ATI driver page, the x1950 works just fine && dandy with recent fglrx releases.

I've since grown tired of waiting for ATI to get in gear and support AIGLX, so I moved to an Nvidia 8800 GTS board, and the x1950 is being bought by a friend building a budget WIndows-only system for gaming.

Nvidia's been much smoother thus far.

---

### Post by Exuus on 2007-07-27
So, if I use envy to install and set up my drivers, followed by making use of the guide previously posted, this should then let me have compiz fusion?

---

### Post by Exuus on 2007-07-27
Aaaaaaand. . . . .. it works!

Thanks to everyone who helped me get compiz working, you've all helped convert another windows user across to Ubuntu. Now all that remains is for me to go tinker (and probably break something else :p ).

Once again, thank you all for your help.

---

