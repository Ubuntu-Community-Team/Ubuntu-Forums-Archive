---
title: "save hard drive space?"
date: 2009-03-02
forum: General Help
---

### Post by sansa dude on 2009-03-02
ok i have an old laptop with only a 10gb hard drive now i found out i only have 2.7 gbs avalible just after i installed xubuntu i had 6.6 but then after i installed a couple programs, and installed updates and loaded a little less than 1 gb of music ive got 2.7 gb is it the updates that installed so much? i really only installed a few programs (inkscape, virtual box and some other things) i also updated open office which i will use. when i try to untinstall some programs i won't use it says other programs need them (eg. bluetooth) any suggestions?

---

### Post by cariboo on 2009-03-02
Open a Applictions-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and

```
sudo apt-get autoremove
```

This will clean out archived packages in /var/cache/apt/archives and remove any unneeded dependencies.

This should help you gain some free space on your hard drive.

Jim

---

### Post by phr33k-dc on 2009-03-02
thats class got lots of free space!

thanks man

---

### Post by thtrgremlin on 2009-03-02
So just getting things straight, you got a 10g hard drive which I am going to guess has 8g root and 1g swap. you installed xubuntu, updates + inkscape and virtualbox + 1gb of music leaves you with 2.7g free space?

For one thing, gb are measured different in advertising than how it shows up in your computer (I hate that). so your 10 is really about 9, so take away maybe 1g of software and 1g of music makes 7g, and ubuntu averages 3.5g or so + 1g swap would make 2.5g free?

so you have more free space than I would estimate in your situation, however some things that can help:

1) ```
sudo apt-get clean
```
clears out the apt cache of downloaded packages

2) ```
sudo apt-get autoremove
```
removed unnecessary packages

3) Have you emptied your trash recently?

10gb isn't a lot of space anymore. but for everything to be working, that should be enough space for your own work, unless you just want to fill it with music... then you could run out pretty quickly.

Not sure what else can do with a fresh install other than either upgrade, or get an external drive to keep all your stuff on.

---

### Post by sansa dude on 2009-03-02
ok thanks for the quick responces ive just removed a few more programs but i want to uninstall some others that i wont use (eg. thunderbird, abi word etc.) and yes the hard drive is formated to 9 gb is there a way i can delete the swap or the extra boot options like when i boot up and press esc or something and it shows me more ways to boot the system. i will run the comands suggested above see if that clears anything up!

---

### Post by Slim Odds on 2009-03-02
Reduce the "reserved" space with tune2fs.

Use the -m option

---

### Post by spcwingo on 2009-03-02
You can also install localepurge to remove unused locales.

```
sudo apt-get install localepurge
```

---

### Post by Slim Odds on 2009-03-02
> **spcwingo said:**
> You can also install localepurge to remove unused locales.

```
sudo apt-get install localepurge
```

So how much space are we talkin' here?

---

### Post by sansa dude on 2009-03-02
> **Slim Odds said:**
> So how much space are we talkin' here?

im on a 10gb hard drive and i need to uninstall some applications

---

### Post by spcwingo on 2009-03-02
> **Slim Odds said:**
> So how much space are we talkin' here?

I'm not really sure, but my entire install only takes up a little over 1 GB, although I didn't install Xubuntu.  I installed the cli and built from there, so your mileage may vary.

---

### Post by sansa dude on 2009-03-02
oko i tried the 3  that were  suggested and the first one didnnt do any thing the 2nd one  only uninstalled 17mbs of data and the 3rd i didnt know what to do in it cause i didnt want to select any thing that  could be wrong

---

### Post by Slim Odds on 2009-03-02
> **sansa dude said:**
> im on a 10gb hard drive and i need to uninstall some applications

I was talking about this:
```
sudo apt-get install localepurge
```

---

### Post by sansa dude on 2009-03-02
> **Slim Odds said:**
> I was talking about this:
```
sudo apt-get install localepurge
```

ohh ok i don't know what to do in that one when it came up

---

### Post by Slim Odds on 2009-03-02
localepurge sounds a wee dangerous:```
Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.
```

---

### Post by sansa dude on 2009-03-02
> **Slim Odds said:**
> localepurge sounds a wee dangerous:```
Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.
```
  i guess its a good  thing i didn't mess  around in there just yet

---

### Post by spcwingo on 2009-03-02
I have had ZERO of the above mentioned problems with localepurge...who knows, maybe I'm just one of the lucky ones.

---

