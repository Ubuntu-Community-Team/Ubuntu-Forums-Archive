---
title: "HowTo: Install i386 DEBs in LPIA Dell Ubuntu Mini 9"
date: 2008-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakker.yak on 2008-11-14
[B]UPDATE: This is no longer necessary. The Dell Ubuntu 8.04 has been updated and the new version of Gdebi will enable you to install i386 DEBs into your LPIA system.

If you need to fix your system from a previous attempt to update GDebi, 1) below may still be applicable to you as a fix.[/B]

Ok, (finally) received my Mini yesterday and had a chance to test this out.

This is to enable you to easily install i386 DEBs (Skype, Opera, etc.) into your LPIA Dell Ubuntu using point-and-double-click of the DEB files. 

If you previously downloaded and installed
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)

chances are that you now have a broken system and can't install anything (getting error messages about broken dependencies).

If this is you, go to 1) before 2)

If this is your first time trying to get i386 DEBs to work on your LPIA Dell Ubuntu, go to 2)


1) Restore your system back to the default version of gdebi-core

Open-up Synaptic: System->Administration

Search for 'gdebi'

Select 'gdebi-core' so that it's highlighted

Select 'Package'->'Force Version...' from the menu

Select '0.38 (hardy)' to downgrade the package

You should now have the default 0.38 (hardy) versions for both gdebi and gdebi-core


2) Upgrade both gdebi and gdebi-core to newer versions

These newer versions are not yet available in the Dell Ubuntu repositories, but should be there eventually (see [https://bugs.launchpad.net/dell-mini/+bug/297018](https://bugs.launchpad.net/dell-mini/+bug/297018) to track status)

Create a new directory called CustomDebs in your home directory

Download the following and put them into the CustomDebs directory
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi_0.3.8netbook1_all.deb)

Open-up Synaptic: System->Administration

Search for 'dpkg-dev' and install it. Close Synaptic.

Open-up Terminal: Accessories->Terminal

Copy-and-paste each of the following at the command line, one line at a time (press Enter after each):

```
cd CustomDebs
find . -name "*.deb" > overridefile
dpkg-scanpackages . overridefile > Packages
sudo gedit /etc/apt/sources.list

```

The last line will launch a text editor.

Edit sources.list by adding the following line at the the end of file:

deb file:/home/<user>/CustomDebs ./

Replace <user> above with your actual username

Save and close sources.list.

Open-up Synaptic.

Click on the 'Reload' button in the upper, left-hand corner.

Search for 'gdebi'

Right-click on the 'gdebi' package and select 'Mark for upgrade'. This should also auto-highlight for you the gdebi-core package which is a needed dependency for gdebi.

Click on the 'Apply' button

Double-check the warnings and packages. You should get warnings about the packages not being authenticated and that you will be replacing the existing gdebi with a newer version. If there's something that looks suspect, don't continue. Post a question before trashing your system.

After the changes are applied, you should have the latest version of gdebi and gdebi-core. You should now be able to double-click on i386 DEBs and install them into your LPIA system. Tested with Skype.

---

### Post by starcannon on 2008-11-14
Nice guide thanks. If its on a per package basis that one has downloaded, then for example:
```
sudo dpkg -i --force-architecture skype-debian*.deb
```
works very nicely as well, I was installing skype in this example, but it should work equally for most packages.

GL and have fun.

---

### Post by yakker.yak on 2008-11-14
Thanks. My understanding with dpkg --force-architecture was that it made it difficult to manage/remove the package afterwards (i.e. doesn't show up in Synaptic).

Correction: just checked whether Skype shows up in Synaptic and it does not.

---

### Post by starcannon on 2008-11-14
ah I didn't know about that, not sure of the dpkg deinstall or purge flags would work or not, though I won't be removing skype anytime soon as its one of the "must haves" for me"; good to know though as its nice to know what one is getting into.

Thanks again

---

### Post by starcannon on 2008-11-14
Heres something that may be of use when uninstalling forced software:
```
sudo dpkg -l {partial or full package name}
```
And in my case Skype did show up, though I haven't tried to remove it.

---

### Post by yakker.yak on 2008-11-14
> **starcannon said:**
> Heres something that may be of use when uninstalling forced software:
```
sudo dpkg -l {partial or full package name}
```


Thanks. Yup, that also lists my Skype install via Gdebi.

I wonder if it's not showing up in Synaptic because the package is i386 and Synaptic is only displaying lpia packages.

Normally (on an i386 system) doing an install via Gdebi results in that package showing up in Synaptic.

---

### Post by RichTJ99 on 2008-11-14
Yak,

So your method allows for the installation of debs but not the uninstalling?  Either way its good news to me.

BTW, are you able to use clonezilla on your mini?

Thanks,
Rich

---

### Post by yakker.yak on 2008-11-14
> **RichTJ99 said:**
> Yak,

So your method allows for the installation of debs but not the uninstalling?  Either way its good news to me.

BTW, are you able to use clonezilla on your mini?

Thanks,
Rich

Yes, you can remove packages installed via the above Gdebi method, just not via Synaptic, but using dpkg. For example, you can open up Terminal and type

```
sudo dpkg --remove skype

```

which will remove skype. Just make sure to get the name of the package correct. Use dpkg -l <package name> to check the name.

Haven't used Clonezilla, sorry.

---

### Post by starcannon on 2008-11-17
Skype and other packages, there appears to be a better way; check out this thread:
 				 				[**HOWTO: Repackage i386 deb for in lpia (for Dell Mini9)**]("http://ubuntuforums.org/showthread.php?t=962835") 			

Enjoy.

---

### Post by yakker.yak on 2008-11-17
Thanks. I have seen that method, although I'm not sure how you mean that it's better -- going that route would mean that you would need to repackage each and every i386 DEB that you want to install, whereas using Gdebi is point-and-click install once you've gone through the process of updating your Gdebi.

The one benefit I could see to a complete repackage of each DEB would be that you will end-up changing the architecture field to lpia so maybe it will show up in Synaptic for management and removal.

---

### Post by gavinfoxx on 2008-11-19
Uh, when I search for gdebi in synaptic package manager, nothing comes up.  What did I manage to break or remove to cause this?

---

### Post by feranick on 2008-11-21
> **yakker.yak said:**
> 
The one benefit I could see to a complete repackage of each DEB would be that you will end-up changing the architecture field to lpia so maybe it will show up in Synaptic for management and removal.

That is precisely why using the modified GDebi is not any better than using the --force-architecture flag. One of the deb packaging system strengths is the ability to track the installed packages with a package system (like synaptic). If those packages don't show up you cannot update them, and removing them can be painful for the unexperienced user. 

Bottom line: [repackagingva i386 package into a lpia]("http://ubuntuforums.org/showpost.php?p=6058820&postcount=1") is the most transparent way, although not the simplest. Using the modified Gdebi is simpler, but not the most transparent, and certainly not the most recommended.

---

### Post by feranick on 2008-11-21
> **gavinfoxx said:**
> Uh, when I search for gdebi in synaptic package manager, nothing comes up.  What did I manage to break or remove to cause this?

The workaround in this tread does not come trouble free. With the new Gdebi you are effectively using the --force-architecture flag. What this means is that the packages you install do not show up on Synaptic.

A better, more laborious way to do this is by [repackaging the debs]("http://ubuntuforums.org/showpost.php?p=6058820&postcount=1"), not simple, but safer.

---

### Post by vegetarianshrimp on 2008-12-28
Umm...I did it, but I think it has created some problems. Do you know how to un-do this?

---

