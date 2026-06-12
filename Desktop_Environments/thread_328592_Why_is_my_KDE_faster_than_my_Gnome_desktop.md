---
title: "Why is my KDE faster than my Gnome desktop?"
date: 2006-12-31
forum: Desktop Environments
---

### Post by wersdaluv on 2006-12-31
I am running both Kubuntu and Ubuntu in this laptop but Kubuntu is significantly faster. Whenever I scroll windows up and down with Ubuntu or I move windows from one place to another, it is very slow. It has always been the case that's why I decided to settle with Kubuntu instead. I don't know the reason because I'm not running any additional desktop effect with Ubuntu and I believe that all drivers that are installed in my Kubuntu desktop are installed in my Gnome desktop as well.

I think Ubuntu should run a little faster. Why is it this way? What can I do?

---

### Post by maxamillion on 2006-12-31
I haven't the slightest clue why gnome is running slower than kde and I believe this to be a rare occasion. I might recommend checking out xfce4 if you are interested in speed.

```
sudo aptitude install xubuntu-desktop
```

---

### Post by ciscosurfer on 2006-12-31
> **wersdaluv said:**
> I am running both Kubuntu and Ubuntu in this laptop but Kubuntu is significantly faster. Whenever I scroll windows up and down with Ubuntu or I move windows from one place to another, it is very slow. It has always been the case that's why I decided to settle with Kubuntu instead. I don't know the reason because I'm not running any additional desktop effect with Ubuntu and I believe that all drivers that are installed in my Kubuntu desktop are installed in my Gnome desktop as well.

I think Ubuntu should run a little faster. Why is it this way? What can I do?This seems to be a common perception.  Which isn't to say it is merely a perception: KDE probably does run faster than GNOME.  Why?  I don't have a technical answer, but I've noticed this as well.  I suppose KDE components just work better together than GNOME components, hence the faster speed.

I know that isn't exactly what you were looking for in terms of a answer, but I've come across this as well and thought I'd add my input. :D

If you're looking for sheer speed, than there a number of other window managers you can check out that run much faster than KDE or GNOME, fluxbox and openbox are two to name a few.

---

### Post by wersdaluv on 2006-12-31
I think I didn't state my point well. In my laptop's case, whenever I scroll up and down windows running in Ubuntu, it is so damn slow and I really mean it but this problem is not present in my Kubuntu desktop.

---

### Post by qalimas on 2006-12-31
> **ciscosurfer said:**
> This seems to be a common perception.  Which isn't to say it is merely a perception: KDE probably does run faster than GNOME.  Why?  I don't have a technical answer, but I've noticed this as well.  I suppose KDE components just work better together than GNOME components, hence the faster speed.

I know that isn't exactly what you were looking for in terms of a answer, but I've come across this as well and thought I'd add my input. :D

If you're looking for sheer speed, than there a number of other window managers you can check out that run much faster than KDE or GNOME, fluxbox and openbox are two to name a few.

I believe it is due to GNOME using separate things for each task.  In KDE, once you load Konqueror, you have your file manager, web browser, etc all loaded into RAM.  I have noticed no difference in speed between KDE and GNOME though, I just prefer the KDE look and feel.

---

### Post by riven0 on 2006-12-31
> **wersdaluv said:**
> I think I didn't state my point well. In my laptop's case, whenever I scroll up and down windows running in Ubuntu, it is so damn slow and I really mean it but this problem is not present in my Kubuntu desktop.

Well... do you have the official graphic drivers installed for your lappy? That'll help.

---

### Post by glenndavy on 2006-12-31
just bumping to say likewise here. these arent issues with "raw speed", just gnome in general seems to have lots of moemntry bottlenecks. having just replaced kubuntu on my laptop wtih ubuntu. Often when typing in gnome, cursor will appear to freeze for perhaps 3 secs then all my typing will suddenly appear. even non-gnomish unrelated things like opening a text file of few K inside terminal with vi - used to be instant (as you'd expect) in kbuntu, but now I have a delay of several seconds before vim opens doc. i agree with OP that scrolling windows can be particularly frustrating.

---

### Post by wyth on 2007-01-12
This is one of the reasons I went back to Kubuntu after trying Ubuntu Edgy.  Given the religious fervor many seem to have about these issues (Gnome is obviously faster and if you don't see that you're an idiot/KDE is obviously faster and if you don't see that you're an idiot/speed is all an illusion of perception and if you don't see that it's because it's an illusion of perception), I think one obvious answers is simply hardware.  That is, Gnome will run better on some hardware than KDE, and KDE will run better on other hardware.  In my case, since Breezy, KDE has always run faster on my laptop.  On my desktop, it was nearly equal, but there was again a bit of a lag with Gnome that KDE seemed to lack -- and I say seemed because if it was a perception or not, it doesn't matter.   I'm taking Aritstotle's epistemilogical viewpoint on this, not the Platonic world of ideals; that is, seeing is believing.

---

### Post by Erunno on 2007-01-12
> **qalimas said:**
> I believe it is due to GNOME using separate things for each task.  In KDE, once you load Konqueror, you have your file manager, web browser, etc all loaded into RAM.  I have noticed no difference in speed between KDE and GNOME though, I just prefer the KDE look and feel.

Err, nope. Konqueror is a kparts viewer (the component framework of KDE). Kparts are loaded into konqueror when needed. Konquror in itself is a very slim application.

---

### Post by studiesrule on 2007-01-12
I learnt another factor is what are you running in the background? KDE has a lot of back-end that load up in the beginning. GNOME has much fewer of such. GNOME apps aren't slowed down that much when running in KDE because they don't have to load a lot of stuff. Whereas, KDE apps have to boot up a lot of stuff (just open up top/ SysGuard and look for all things beginning with a K). Maybe your running KDE apps in your GNOME distro? 

On another note, when I tried out Xubuntu 6.06, I had a lot of performance issues on a clean install. I made a point not to install anything GNOME and especially anything KDE. Is it just me?

---

### Post by der_joachim on 2007-01-12
Which login manager do you use? When I use KDM, XFCE is noticably slower than when I use GDM.

---

### Post by amk221 on 2007-01-20
I've noticed kde is faster than gnome too, its strange, because its visually more appealing and graphically intensive than gnome, so who knows why.

---

### Post by Amt0571 on 2007-01-20
I like gnome more, but my experience tells me that in older machines KDE tends to be a much better option. On a PIV2.8 I'm running gnome perfectly even with Beryl, however, on an Athlon 1,4 I decided to install KDE since gnome was, at best, sluggish (switching tabs in firefox was sloooooooooow, and resizing a window a pain).

I still don't know what may cause this... I even thought it may be my old system, but it seems it's just gnome that needs more horsepower...

By the way, I don't think that KDE is more eye candy than gnome... gnome is just as beautyful as KDE (in fact, I like gnome more from a sthetic point).

---

### Post by Kindred on 2007-01-20
KDE is definitely faster than Gnome for me, the difference in screen redraw speeds is really quite noticeable also - KDE (Qt) is far better in this respect.

---

### Post by mexlinux on 2007-01-20
OK, we all agree KDE is faster.
Then once again I have to ask (flame me), why is not KDE the default desktop in ubuntu?

---

### Post by Amt0571 on 2007-01-20
> **mexlinux said:**
> OK, we all agree KDE is faster.
Then once again I have to ask (flame me), why is not KDE the default desktop in ubuntu?

Well, I agree it's faster but there are other things that matter. Gnome is more organized in my opinion (yes, I know it's the typical usability story), and with a 2ghz machine the difference in speed isn't noticeable.

Also some of the KDE apps are not mature enough in my opinion: krita is slow as hell and quite unstable, the same for Karbon 14 (compared to Inkscape) and in general the whole KOffice leaves a lot to be desired nowadays (altough, of course, they are improving things). An important problem is also that Adept is nowhere near Synaptic: the latter is better organized and more useful. This is important since Ubuntu is meant to be used by people who don't like using a terminal.

However I don't think there's any problem with Gnome being the default of Ubuntu: KDE is the default of Kubuntu, just choose the one you like more. I use both (KDE on the "old" machine, and Gnome in the new one).

In the end, I think the biggest problem is the lack of integration between the two: in Gnome I always have Amarok, or Scribus, or something KDE open... and in KDE I have GIMP or Inkscape... I think that this is the only real problem of having 2 different desktops.

---

### Post by patrickfromspain on 2007-01-20
If you have ubuntu and kubuntu in different partitions, I'd check that both are using the same video drivers.

If it is the same but with 2 desktops then I'd try to test both ubuntu and kubuntu each on a separate partition. Maybe there's something running not fine in your setup or whatever.

---

### Post by encho on 2007-01-22
> **mexlinux said:**
> OK, we all agree KDE is faster.
Then once again I have to ask (flame me), why is not KDE the default desktop in ubuntu?

It is default in Kubuntu :p 

Seriously, I do not get why huge majority of people is using Gnome. I know some were saying that it has 'windows' feeling to it, but I just do not feel that way. You can organize your panels/fonts/color schemes/themes/icons for both Gnome and KDE however you like it. It can look like Windows, Mac, even Commodore64 or ZX Spectrum (am I the only one who remembers them) :lolflag: 

So it is just matter of swallowing your pride and going with better desktop. At this moment it is KDE. And with upcoming QT4 base it is going to be at that position, for some time.

Just my opinion, however.

---

### Post by glenndavy on 2007-01-22
Speaking as a KDE user... I think gnome is a good choice of default desktop. I can give gnome to my grandma, my wife, or non geek mate and they'll get around, and everything will just work for them. Its smooth, elegant, it works - the philosophy of 'sensible defaults' works well for that use case IMHO. it means they dont get overwhelmed by choice, options or can readily change things and for get what they've done.

For the rest of us there's apt-get install kubuntu-desktop. Everyones happy that way and no ones dis-enfranchised. BTW  Im hanging for kde 4 - anyone checked it out?

---

### Post by Amt0571 on 2007-01-22
Well, I feel comfortable using both, but there's something I really really miss on KDE: Deskbar! altough I have to admit I miss SuperKaramba and Kpdf on Gnome...

Also I think Konqueror is very good as a browser, but it's not as good as Nautilus as a file manager.

I think that if I had to choose one to use during the rest of my life I couldn't do it... I switch between one and the other when I'm tired... nowadays, I prefer gnome hehehe

---

### Post by tomane on 2007-03-30
I also find KDE to be, how to say it, more responsive than Gnome.
It might not be actually *faster*, it's more related with the response of the DE to user input, eg, menus popping up with icons already loaded, dialog boxes react more promptly to user stimulae, etc.
I haven't touched gnome for some time now, but when I used to use both DEs that's how I felt between gnome and KDE.

cheers,
--to

---

### Post by stokedfish on 2007-03-30
Well, a current KDE needs fewer RAM than a current Gnome, the same for the apps. And with QT4 this will get even better. So, this is no surprise, really.

---

