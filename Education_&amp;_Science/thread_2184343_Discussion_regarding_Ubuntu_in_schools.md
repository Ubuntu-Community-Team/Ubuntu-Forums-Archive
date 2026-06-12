---
title: "Discussion regarding Ubuntu in schools"
date: 2013-10-28
forum: Education &amp; Science
---

### Post by Steve_Cline on 2013-10-28
At our high school we have some older Dell netbooks that have 16gb SSD hard drives.  Windows is problematic because it quickly fills up the user profiles and makes them virtually unusable.  We had Chromium on them but since Google stopped supporting that build we are having more trouble with them.  I have proposed to our IT people that we should look at some version of Ubuntu for them since we only need them for browsing capability and production of documents via Google Drive.  They are hesitant due to security concerns and a general lack of familiarity with Linux.  There are a few people in the IT department who are open to this idea but not enough.  As it stands now, it is very difficult to use the lab but it seems like Ubuntu might resurrect them for a few more years and save us some money.

Has anyone tried installing Ubuntu on a netbook lab at a school like this?  If so, how has it worked and what can I do to deal with some of the security concerns?

---

### Post by buzzingrobot on 2013-10-28
I've no experience with that kind of hardware, but 16gb is not a generous allotment for Ubuntu, either.  If all files are going to be stored at Google, not locally, you might take the angle of a stripped-down Ubuntu install.  Pulling a lot of the apps might also ease the security concerns.

---

### Post by cdaver on 2013-10-28
IDK what your experience level with linux is but after years of using linux I can assure you of one thing. You will need to get your hands dirty. 
By this I mean open up the terminal and start firing commands. (that you may or may not fully understand)

 Also, The latest versions of ubuntu work great with new hardware but often dissapoint when installed on dated hardware.

Based on the 16GB ssd i would say go Ubuntu 10.10 or light weight distros like puppy linux or mint.

If everything is driven via Google Drive all you really need is a browser and some runtime cache. I think 16GB should cover it.

Do not try to install any of the latest distros like Ubuntu 13X.

And if you can point out what your security concerns are perhaps we can provide insight.

If you are using Google Drive, it maintains the security for your documents using your integrated gmail password.

If you mean is ubuntu secure from viruses, etc. Its Linux. No Viruses. No need for antivirus.

---

### Post by buzzingrobot on 2013-10-28
Ubuntu 10.10 is an old release that is no longer supported -- no security patches, no bugfixes -- assuming you could find an install image.  The ability of contemporary applications to run on that old platform would have to be considered.

Mint is an Ubuntu derivative that generally isn't considered a "light" distro.

Ubuntu has the advantage of being supported by an actual business with a good track record of support. That might ease the minds of some of the folks who have security concerns, especially compared to more hobbyist-style distros that are maintained by a few individuals.

Ubuntu 12.04.03 LTS, the current long-term release, will receive updates until 2017.  Support for 13.04 and the current 13.10 release is less than one year.

---

### Post by Alienman24 on 2013-10-29
I have been using Lubuntu with my First graders and my wife's 4th graders.  Chrome works fine (although you have to go to the chrome website to download the .deb file and then open it with gdebi.  The machines they are using are 8gb Asus eeepc's with 1gb of ram.  The Ram will probably be more of an issue than the HD, Lubuntu only needs about 8gb.  Security wise, as long as your rootpassword is something secure, it should prevent them from causing too much damage.  Let me know if you have any questions.

---

### Post by Lars Noodén on 2013-10-29
Both Ubuntu and Lubuntu need less space on the HD (or SSD) than that.  My current Ubuntu 13.10 amd64 desktop takes only 4.8GB on the SSD.  Lubuntu is about the same or less.  On the Lubuntu project's web page, it lists 4.3  GB as the min.  I've also seen others run Ubuntu (or a variant) on notebooks to good effect.  

As mentioned above, the RAM is good, but more is better.

Edit: I just checked a basic Lubuntu installation and it takes 1.9 GB on the HD.   You'll have to add LibreOffice and Gimp and others but those don't take an enormous amount of space at all.

---

### Post by Lars Noodén on 2013-10-29
About the security question, check this wiki page:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Ubuntu has a better track record than what you are replacing, but new == scary for some.

---

### Post by King Dude on 2013-10-30
Lubuntu 13.10 should work really well on archaic hardware. You may want to format the SSD in Btrfs, because it's a little more optimized for SSDs, but since it's only 16GB the performance gains may be minimal at best.

Also, they should think about setting up a small network datacenter. That way users can store their pictures, documents, and other small files in the datacenter rather than on the computer's main drive. Not only will all the files be backed up, but it will also save valuable space on the computer's SSD.

---

### Post by gnuman on 2013-11-20
Haven't been checking in very often lately, but I finally have a Linux lab of my own, after years of pushing for one.  Students love it, as the older Dells are super fast with Xubuntu on them.  We are in a "quarantined" part of our district network, but that only affects us trying to access district machines.  Our web access is great, and we get to learn a lot about networking writing Python scripts and experimenting here and there.

Amazing how much easier it is to teach Comp Sci using Xubuntu.  If they made me go back to Windows or OSX, I'd probably retire early.  :-)

BTW, I totally agree about getting into the terminal and getting comfortable with it.  We don't have static IPs for our student machines, so I've learned a lot about network administration via SSH and a TON about DNS and Bind.

---

### Post by serge.a.123 on 2013-11-27
If we are talking about using Ubuntu in schools, I just want to point out kids safety issue.  I set Ubuntu 13 for my daughter (10 y.o.).  Was I surprised when I opened lenses and typed GIMP to show her the editor - some things that came up in one of the shopping lenses - would not call them exactly age appropriate.  I wish there was some sort of safety filter.  I am yet to do my research for that but so far I didn't find any.

It looks like I can disable this through Privacy option in Ubuntu settings. Going to try this when I am home.

---

### Post by kurt18947 on 2013-11-27
> **serge.a.123 said:**
> If we are talking about using Ubuntu in schools, I just want to point out kids safety issue.  I set Ubuntu 13 for my daughter (10 y.o.).  Was I surprised when I opened lenses and typed GIMP to show her the editor - some things that came up in one of the shopping lenses - would not call them exactly age appropriate.  I wish there was some sort of safety filter.  I am yet to do my research for that but so far I didn't find any.

It looks like I can disable this through Privacy option in Ubuntu settings. Going to try this when I am home.

Sorry to hear about your experience.  I wonder if you should make someone at Canonical aware, perhaps they could tweak something to preclude others having the same experience.  Yes, I believe there's a privacy setting that you can disable web searches.  You could also look into using an alternative desktop.  I use gnome-shell in lieu of Unity and don't get the Amazon search output.  Xubuntu & Lubuntu don't display non-local searches either.

---

### Post by alan-pater on 2013-12-21
Apparently there are still builds of Chromium OS out there: [http://chromium.arnoldthebat.co.uk/](http://chromium.arnoldthebat.co.uk/)

Apart from that, I agree that Lubuntu should be reasonable.

As for the resistance from the IT folks, just tell them that it ain't so hard. If they can manage using blackberries at work and iPhones at home, they can manage running Linux.

---

### Post by Bucky Ball on 2013-12-21
> **serge.a.123 said:**
> If we are talking about using Ubuntu in schools, I just want to point out kids safety issue.  I set Ubuntu 13 for my daughter (10 y.o.).  Was I surprised when I opened lenses and typed GIMP to show her the editor - some things that came up in one of the shopping lenses - would not call them exactly age appropriate.  I wish there was some sort of safety filter.  I am yet to do my research for that but so far I didn't find any.

It looks like I can disable this through Privacy option in Ubuntu settings. Going to try this when I am home.

> **kurt18947 said:**
> Sorry to hear about your experience.  I wonder if you should make someone at Canonical aware, perhaps they could tweak something to preclude others having the same experience.  Yes, I believe there's a privacy setting that you can disable web searches.  You could also look into using an alternative desktop.  I use gnome-shell in lieu of Unity and don't get the Amazon search output.  Xubuntu & Lubuntu don't display non-local searches either.

Off topic. Please get back on topic. There is no way a full blown Ubuntu with shopping lenses will run on these dinky machines. If you have security concerns, please post them in the ***Security Discussions*** section. 

Does make my day, though, that the school is running Win and Google products then states they're worried about security! Then someone else suggests installing a totally obsolete 10.10 release. ;) :-k

I suggest, yes, you do need to get hands dirty. Do some planning, create a mini-install with a lightweight desktop environment and only the apps you are going to need. Create an ISO of the install once you're done and install it to all other machines. This is going to take some work to get right, but they're not going to be very convinced of anything unless you have a feasible and convincing plan. 

Puppy Linux or Porteus may do the trick. There is the option of getting every kid to buy (or supplying them with) a USB stick, installing a lightweight OS with persistence to that with a small partition for any personal data. To use, kid sticks in USB dongle, boot machine from it, there's their own OS with their own customisations. Back up to the cloud at the end of each day (or when appropriate). Puppy Linux would be perfect for this.

Using this method you don't need to install an OS to the machine at all. Files are backed up to the ether, not the machine, and you can keep backups of the USB dongles in case one is lost and a kid just can't live without their customisations! (Or can't be bothered redo-ing on a replacement, vanilla dongle).

I like the USB option and would probably go that way, or at least pursue it until convinced it either was or wasn't going to work.

---

### Post by mips on 2013-12-23
Would Peppermint OS not be a viable alternative?

[http://peppermintos.com/](http://peppermintos.com/)
[http://en.wikipedia.org/wiki/Peppermint_Linux_OS](http://en.wikipedia.org/wiki/Peppermint_Linux_OS)

---

### Post by hsweet2 on 2014-01-06
I did not read all the comments, so this might be redundant.

My colleague and I have run Ubuntu/Edubuntu thin clients on our lab (his now, I am retired) for 6 or 7 years, on the oldest crap in the school.  With it we have done Cad, heavy graphics, programming and more stuff than the rest of the Windows school could dream of.  Do not think of using old boxes as computers, find out about LTSP and learn how to use them as thin clients.

As for security.  The school maintains a filter.  Yours does too I expect. We used openDNS for the time we were somehow out of that loop.  More than that, only one installation to maintain for the whole lab.  I've installed software for the lab between bells (4 minutes) and the kids were all using it that period.

Beyond that, I was able to build a reverse firewall to keep kids out of the computers entirely or just off the web or just on the web but only on chosen sites, or anywhere the school's filter allowed.

You run the sexiest newest version of Ubuntu you want or stick to solid 12.04.  All the clients run that as thin clients, even if they can't run that as a full blown computer.

There is an endless supply of old computers the rest of the school does not want.

I've been in the business of computers in schools since the DOS era.  Nothing I ever used came close in terms of control, usability or security.

---

### Post by hsweet2 on 2014-01-06
Setting up Ubuntu for a school lab is a very different animal than a home set up, in a lot of ways.  I've done both. Kids in both places. (Same for Windows and Macs, really).   For one thing, most schools maintain a filter (and pay for it and folks to keep it working) which you probably do not have on a home system.  So your daughter would see things at home she could not see at school, regardless of the OS. While I did have occasional issues with kids finding their way into places they should not have been, by far the bigger issue for me has been that computers in schools are a 2 edged sword, with distractions of all sorts getting in the way of education.  This would include such mundane things as kids yanking wires for a joke, playing games, watching videos and so on.  

Anyhow, there are some filters you can install at home (forget the name, check out software center), but this really has little to do with a school situation.

---

### Post by younggeek1 on 2014-01-11
Go with very light wheight distos. Try Lubuntu. I'm not sure of the other specs, it should work fine.

---

### Post by morty71 on 2014-01-19
In our english institue, they have ubuntu 5 installed on the systems and it's been working since the day I signed up there !!!
The best way to convince them is installing ubuntu on your own box and showing them the features and how it works. They'll love it...

---

### Post by zgornel on 2014-01-28
I would recommend a new distribution with a lighter desktop environment. You could try the manjaro netbook edition [http://manjaro.org/2014/01/25/1st-release-candidate-of-manjaro-netbook-0-8-9-available/](http://manjaro.org/2014/01/25/1st-release-candidate-of-manjaro-netbook-0-8-9-available/)

---

