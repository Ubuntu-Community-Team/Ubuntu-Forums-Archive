---
title: "Fedora Core 4 Test 1: First Impressions"
date: 2005-03-15
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2005-03-15
FC4t1 is out today. I want to give it a test. I'll actually be installing on AMD64 this time, because I want to see the 'major improvements' GCC 4.0 brings to the k8 architecture (According to Gentooers, of course!)

This thread will be edited as I proceed through the install process:


**Initial Install:**
 I'll be doing a network install, since my caps recently got bumped to 550KB/s!!

Anaconda still looks roughly the same -- a new icon here and there, but it's still the same beast. 

I see that the AMD64 version is installing both i386 and x86_64 packages for practically everything... Hopefully this means better compatibility for us AMD64 users.

Currently waiting for install to finish...

---

### Post by jdong on 2005-03-15
Urg, not worth the time.... Not enough time to go around randomly testing OSes.

---

### Post by jdodson on 2005-03-15
[QUOTE=jdong]Urg, not worth the time.... Not enough time to go around randomly testing OSes.[/QUOTE]

so it failed?:)

---

### Post by jdong on 2005-03-15
There was 70 minutes remaining, I was bored, and I had an essay to write..... Plus, I needed to test the Warty Firefox backport!

---

### Post by jdodson on 2005-03-15
[QUOTE=jdong]There was 70 minutes remaining, I was bored, and I had an essay to write..... Plus, I needed to test the Warty Firefox backport![/QUOTE]

didn't one gnu/linux distro allow you to play solitare while it installed on the machine?  i think that was lycoris...

---

### Post by jdong on 2005-03-15
Gentoo allows me to play 23 hours of solitaire!!!! Beat that! ;)


I'm gonna test Gentoo 2005.0 AMD64, when it comes out. :)

---

### Post by arctic on 2005-03-15
fc4 is a waste of time imho. fedora has always been too buggy and considerably slower than other distros. and this is annoying, although i am not a speed-freak.

...hmmm... why do i still have it on my lappy? i must be a masochist... :D

---

### Post by burlap on 2005-03-15
I am really curious... I was about to use FC3, but after a week of struggle and final disaster with ndiswrapper I decided to give Ubuntu a shot.

And you know what? 

I am really happy.  :grin:

---

### Post by crane on 2005-03-15
I never got FC3 installed. I always crashed half way through the install. I like testing new distros but I don't feel like messing with fedora at all.

---

### Post by darkoptix on 2005-03-15
It took 37min for jdong to realise that Fedora blows ??? :-?

---

### Post by TravisNewman on 2005-03-16
[QUOTE=darkoptix]It took 37min for jdong to realise that Fedora blows ??? :-?[/QUOTE]
 Yeah, you missed a lot about jdong and his Fedora experiences. ;)

It's a LOT more than 37 minutes

---

### Post by Slapdash on 2005-03-16
and to think I was about 1 hour away from trying it  :grin:

---

### Post by jayded on 2005-03-16
I recently moved from FC3 to Ubuntu as my primary workstation OS.
I have good reasons why I like Ubuntu better than FC3 and I wont go into them here.

However, Fedora is still a pretty good distro, I wouldn't write it off so fast.
Why do these threads always turn into *INSERT OTHER DISTRO NAME HERE* bashing ?

Come on guys  :roll:

---

### Post by Lovechild on 2005-03-16
Get off the Fedora bashing, it's a fine distro - as if jdong won't review it, I sure will, I'm burning the FC4test1 cds as well speak, I sadly don't have a fancy amd64 rig to test it on so you'll have to live with x86

---

### Post by jdong on 2005-03-16
I look away for a few hours and it turns into a distro bash... All I said was that I'm too busy to test another distro -- I didn't say anything about Fedora....


Personally, I'm very interested in the distro. :)

---

### Post by Slapdash on 2005-03-16
yep thats the idea I got as well.

I was just making a joke in my comment as well.
I will still test it out as well. I know I hate RPM's though ;)

no seriously I'd like to give it a try.

Maybe it's just a toutchy subject  :-D

---

### Post by ssam on 2005-03-16
ubuntu and fedora are two hot distros at the moment. they have different appoches: apt vs rpm; big install vs little install. but they are also quite similar, both have fast release cycles and hot off the compiler software, new gnomes, kernels, etc.

also the relation between fedora and RHEL seems similar to ubuntu and debian. i imagine some people will strong disagree with me, but that how i see it.

i think a bit of friendly competition is good.

---

### Post by dizzie on 2005-03-16
Whats fedora ? ;)

Sounds like a girlie name or some kinky obsession, or... nah nm :)

---

### Post by Slapdash on 2005-03-16
if you read what people say on Slashdot it looks a bit touch and go to me.... Anyway i like what I have at the moment....

[http://linux.slashdot.org/linux/05/03/16/040240.shtml?tid=110&tid=106](http://linux.slashdot.org/linux/05/03/16/040240.shtml?tid=110&tid=106)

---

### Post by Lovechild on 2005-03-16
Okay, I install Fedora Core 4 test 1now the following are my findings.

It installed nicely, aside some odd switching back and forth between cds something I've never seen with Fedora before - for the first time in my life I've used cd 4.

Okay the bad news, when it first booted, firstboot didn't start because of python issues - so only the root account was present, sadly do to something I'm tempted to attribute to SELinux it didn't save the password I gave it during the anaconda installer. So a reboot with SELinux=0 later and some yum magic to update a few packages I had X and SELinux back.

As usual with the Development branch of Fedora packages don't always install because of conflicts, this happened today as well - so selective updates to avoid the problem library were the only way around the problem - I expect this will be fixed tomorrow.

I selected Danish in the installer, yet LANG=da_DK.UTF-8 wasn't set, and the provided tool fails to set it correctly - very disappointing since Fedora always supported languages well. The config files look okay so where the problem lies I don't know.

Otherwise programs start the same as always, OpenOffice2 is present but the icons and theme stuff hasn't been enabled yet so it doesn't look as nice as it did in OOo1 (or Hoary's OOo2 for that matter).

The desktop theme is bluecurve as always, meaning I'll have to live without clearlooks which was present in Hoary and I like very much - personal preference

Sadly the up2date/rhn-applet replacement pup wasn't ready for the FC4t1 release, I hope it will be ready soon because I like visual confirmation that I have updates waiting - I for one liked the throbbing red icon in the tray in the previous releases, it was noticable.

So what's new:

GCC4 meaning we now have some cool free stuff like Java, and there's a new protective meassure in glibc/gcc generally known as fortification - I'm a big fan of security so more is always welcome and Fedora has always rolled out security by default, like exec-shield, SELinux, a default firewall and now this added protection.

GNOME 2.10, we all know this rocks.. so no need to go into detail here. (I believe KDE 3.4 is also present, but I'm relatively indifferent to KDE so I haven't installed it)

OOo2, again no introduction needed - it still needs polish though.

Fedora Extras, it should be enabled by default now, but I haven't had time to play with it.

Xen, this looks like fun, but I don't personally have a use for it yet - Rik van Riel is doing some hard work beating it into shape I think.

Overall I think, despite these gross issues, that FC4 is looking good, and by all means if you have the time and skills needed, please install it somewhere and start posting bugs.

---

### Post by wbeck85 on 2005-03-16
[QUOTE=dizzie]Whats fedora ? ;)

Sounds like a girlie name or some kinky obsession, or... nah nm :)[/QUOTE]


Its a hat :)

[Like what Indiana Jones wears](http://www.indygear.com/gear/fedora.shtml)

Oh, you were probably kidding werent you? ooops. I can never tell. My girlfriend gets frustrated with me cuz she tries to kid me about stuff and i get all in huff or worried and the joke is ruined. Oh well, hope you like Indy

---

### Post by mike998 on 2005-03-16
I installed FC2 a while back and then FC3 came out and I attempted to use yum/apt to upgrade and it was a total fiasco.  50% of my install broke and the other 50% just did what it wanted to.
RedHat was good, but FCx has become terrible.  Ubuntu is like a breath of fresh air.  :-D

---

### Post by Lovechild on 2005-03-16
[QUOTE=mike998]I installed FC2 a while back and then FC3 came out and I attempted to use yum/apt to upgrade and it was a total fiasco.  50% of my install broke and the other 50% just did what it wanted to.
RedHat was good, but FCx has become terrible.  Ubuntu is like a breath of fresh air.  :-D[/QUOTE]

If you had read the release note you would know that yum isn't a supported upgrade method from FC2 to FC3 - only using the install cds is. Some very important changes were made, which required more logic and complexity than should be build into yum.

---

### Post by earobinson on 2005-03-16
As an ex FC user the diference i see is that fedora had a lot more guis for all the little things (services for one) but to me i found FC3 to be a bit of a flop i will look at FC4 but i will wait till it is done. As for ubuntu it is a great distro yet it could use a bit more gui suport.

---

