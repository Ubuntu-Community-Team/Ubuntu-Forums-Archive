---
title: "how do I ensure that I install a NON-Snap version of an application (Thunderbird)"
date: 2020-01-08
forum: Desktop Environments
---

### Post by pjstock on 2020-01-08
when I reinstalled Thunderbird recently I seem to have inadvertently installed a Snap version 
I barely know what a Snap version is but it has been a nightmare (I cannot access most of my HDDs directly from Thunderbird, I cannot save attachments from an email to most of my HDDs. and apparently this is a restriction or limitation of Snap versions.)

anyway, I want to remove the install I have and reinstall Thunderbird but only if it is a full function NON Snap version.

how do I find or identify a Non Snap version?

many thanks

Peter

---

### Post by CatKiller on 2020-01-08
> **pjstock said:**
> how do I find or identify a Non Snap version?

For precision in a task, the command line is generally the cleanest option. ```
sudo apt install thunderbird
```

The command to remove your snap version would be something like ```
sudo snap remove thunderbird
```

---

### Post by guiverc on 2020-01-09
You didn't give your release of Ubuntu. (some newer releases will be moving to snaps by default for some applications, eg. Chromium browser)

You can use a command like

 ```
"[COLOR=#333333][FONT=monospace]snap connect chromium:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]removable-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]media[/FONT][/COLOR][COLOR=#333333][FONT=monospace]"[/FONT][/COLOR]
```

to grant access of that snap access to certain directories (eg. /media/, /mnt/ etc). 
Note: *Replace* *"chromium" with the name of your snap*

---

### Post by Dennis N on 2020-01-09
> how do I find or identify a Non Snap version?
Neither Synaptic Package Manager nor Apt can install a snap package, so you are "safe" using those. In Ubuntu Software, check the details of any package to see the source (see attachment, which is for Thunderbird).

---

### Post by ajgreeny on 2020-01-09
> **Dennis N said:**
> Neither Synaptic Package Manager nor Apt can install a snap package, so you are "safe" using those. In Ubuntu Software, check the details of any package to see the source (see attachment, which is for Thunderbird).

Except that in 20.04, which I am running as the development version, synaptic package manager, and I assume apt install, will install in an indirect manner the snap version of chromium browser, as the deb version normally available that way is no longer available.

---

### Post by Dennis N on 2020-01-09
> Except that in 20.04, which I am running as the development version...
Wow. That's interesting. Change noted.

> I cannot access most of my HDDs directly from Thunderbird, I cannot save attachments from an email to most of my HDDs.
You need to mount those HDDs in a supported location for snaps. With Chromium, things have evolved. I have been using the Chromium snap for a long while, and access has improved. Previously, I could not access my data partition which was mounted under /mnt from the Chromium snap. Now, I find this is allowed. All is good in Chromium land &#128578;

---

### Post by ajgreeny on 2020-01-09
Yes, just to add that I haven't had any access problems running that snap version of chromium either in 20.04 but it is the only snap version of anything that I've tried so far.

Seems the old snap access problems may be over, or almost so, in 20.04; let's hope so.

---

### Post by pjstock on 2020-01-09
> **guiverc said:**
> You didn't give your release of Ubuntu. 

Apologies

I am running: Ubuntu 18.04.3 LTS

and the only Thunderbird option I see in Ubuntu Softawre is that Snap version.

---

### Post by ajgreeny on 2020-01-09
Open up "Software & Updates" and check that you have both Universe and Multiverse repos enabled in the first tab, then run ```
sudo apt update
sudo apt install thunderbird
``` to install the deb version, and finally run command ```
sudo snap remove thunderbird
``` to remove the current snap version.

I must add that I have no idea where the snap version keeps all the emails that you have received whilst using it so make sure you backup and have copies of any that you need before removing the snap version.

EDIT:
I have just checked in the Software application and see that there are indeed two versions of thunderbird
[LIST=1]
[*]***Thunderbird***, the snap version
[*]***Thunderbird-Mail***, the more usual .deb version which is the one I use.
[/LIST]

---

### Post by TheFu on 2020-01-09
> **ajgreeny said:**
> Seems the old snap access problems may be over, or almost so, in 20.04; let's hope so.

/mnt/ and /media/ are for temporary mounts according to the Linux File System Hierarchy Standards:
[https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s12.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s12.html)
[https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html)

Linux is about flexiblity.

---

### Post by ajgreeny on 2020-01-09
So can we assume that an external disk mounted in a folder in a user's home, either from fstab or by manual mounting, will never suffer the access problems that some users have suffered when using snap packages?

As I said, I have not used snaps so far except for chromium in the dev version of 20.04 so I ask this very much as a new snap user.

---

### Post by pjstock on 2020-01-09
> **TheFu said:**
> /mnt/ and /media/ are for temporary mounts according to the Linux File System Hierarchy Standards:
.

can I force an update to version 20.04?

when I "check for Updates" in settings It comes back telling me that my 18.04.3 LTS is "Uptodate"

---

### Post by CatKiller on 2020-01-09
> **pjstock said:**
> can I force an update to version 20.04?

when I "check for Updates" in settings It comes back telling me that my 18.04.3 LTS is "Uptodate"

20.04 won't be released until April 2020, hence the name. It won't be automatically offered as an upgrade to 18.04 users until the first point release.

---

### Post by Dennis N on 2020-01-09
> **ajgreeny said:**
> So can we assume that an external disk mounted in a folder in a user's home, either from fstab or by manual mounting, will never suffer the access problems that some users have suffered when using snap packages? As I said, I have not used snaps so far except for chromium in the dev version of 20.04 so I ask this very much as a new snap user.

If you mount a partition somewhere in your home folder, I believe there's no problem. You can open & save under /media/<user> and /mnt - at least that works from Chromium and Firefox snaps*.

*Checked in 16.04 and 19.04. I suspect it will work in all releases. See additional comments in post #19 about accessing these locations.

---

### Post by TheFu on 2020-01-09
> **ajgreeny said:**
> So can we assume that an external disk mounted in a folder in a user's home, either from fstab or by manual mounting, will never suffer the access problems that some users have suffered when using snap packages?

As I said, I have not used snaps so far except for chromium in the dev version of 20.04 so I ask this very much as a new snap user.

There are many reasons NOT to do this.  Mainly for backup size management.  It you do want to add storage to a HOME, I'd add it either for the entire /home/ or to /home/username if just 1 userid needs it.  All or nothing to backup requirements are clearer.

Many smart people here also use symbolic links from their HOME to storage mounted elsewhere as a way to expand specific types of storage, while not screwing up backup sizes or versioning.  For example, media files don't tend to change, but having them available from a HOME/videos is convenient.  Especially for photos, music, and videos, this is very handy.  

If following a symbolic link from ~/photos/ to other storage works, great!   A confined web browser is something I'm fully behind, which is why using firejail has been normal here since 2016.

---

### Post by mörgæs on 2020-01-09
If you next time install one of the other Buntus than Ubuntu you will be free from snap by default.

---

### Post by The Cog on 2020-01-09
> **mörgæs said:**
> If you next time install one of the other Buntus than Ubuntu you will be free from snap by default.

Not necessarily. In Xubuntu 19.10, chromium-browser is **only** available as a snap. 
I gather that's true for all variants, and it's the only way Chromium will be available on *buntu in the future.

---

### Post by ajgreeny on 2020-01-10
> **The Cog said:**
> Not necessarily. In Xubuntu 19.10, chromium-browser is **only** available as a snap. 
I gather that's true for all variants, and it's the only way Chromium will be available on *buntu in the future.
That is correct; Xubuntu 20.04 has chromium as a snap only, and as I mentioned earlier in the thread, even if you use **synaptic** (and probably also **apt install**) it will first install a small transitional package which itself then installs the snap version.

---

### Post by Dennis N on 2020-01-10
> You can open & save under /media/<user> and /mnt - at least that works from Chromium and Firefox snaps*.

I should amend the previous post in regard to the above statement. The ability to access these locations was NOT due to some upgrade or improvement in the snaps - it occurred to me later that I had set permissions from within the browsers' web pages in Ubuntu Software. This is what allows the access to /mnt and /media/<username>. The two screenshots below show how: 1) click permissions button, and then 2)  switch on "read/write files on removable devices". It's off by default.

Note: The command in post #3 will produce the same result, but setting switches on the browsers' web pages doesn't require the user to know about or find the special command to do this. 

I left the "Access USB hardware directly" off for now.

---

### Post by TheFu on 2020-01-10
Anyone know if the snapd team's plans to support NFS was ever implemented?  Have a bunch of NFS here and I can't find any media/mount-access confinement controls for snapd.  Found a 12 month long thread about supporting NFS, but it just ended without any statement.  Plus the NFS concern was for HOME directories, not other locations.

---

### Post by mörgæs on 2020-01-10
> **The Cog said:**
> Not necessarily. In Xubuntu 19.10, chromium-browser is **only** available as a snap. 
I gather that's true for all variants, and it's the only way Chromium will be available on *buntu in the future.

Now I have tested in Xubuntu 19.10 and yes, it's indeed the case.

```
sudo apt install chromium-browser
```
installs snapd without asking for permission (!) and installs at the same time chromium as a snap package. 

Both were simple to remove so no harm done but still I would like to receive a clear warning from apt. 

It seems like I have to use the dry run option 
```
sudo apt install <some package> --dry-run
```
every time in the future so I know what is going to be added to my systems.

---

### Post by howefield on 2020-01-10
> **mörgæs said:**
> installs snapd without asking for permission (!) and installs at the same time chromium as a snap package.

Both were simple to remove so no harm done but still I would like to receive a clear warning from apt.

Sure snapd wasn't already installed ?

Installing with snapd already installed

```
hugh@eoan:~$  sudo apt install chromium-browser
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  chromium-browser
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 48.7 kB of archives.
After this operation, 163 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu eoan-updates/universe amd64 chromium-browser amd64 77.0.3865.120-0ubuntu1.19.10.1 [48.7 kB]
Fetched 48.7 kB in 5s (9,446 B/s)         
Preconfiguring packages ...
Selecting previously unselected package chromium-browser.
(Reading database ... 182581 files and directories currently installed.)
Preparing to unpack .../chromium-browser_77.0.3865.120-0ubuntu1.19.10.1_amd64.deb ...
=> Installing the chromium snap
==> Checking connectivity with the snap store
==> Installing the chromium snap
Warning: /snap/bin was not found in your $PATH. If you've not restarted your session since you
         installed snapd, try doing that. Please see https://forum.snapcraft.io/t/9469 for more
         details.

chromium 79.0.3945.79 from Canonical&#10003; installed
=> Snap installation complete
Unpacking chromium-browser (77.0.3865.120-0ubuntu1.19.10.1) ...
Setting up chromium-browser (77.0.3865.120-0ubuntu1.19.10.1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
```

And without snapd already installed, there is a clear warning as is usually the case when apt wants to install packages other than those explicitly asked for. 

```
hugh@eoan:~$  sudo apt install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  snapd
The following NEW packages will be installed
  chromium-browser snapd
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 18.8 MB of archives.
After this operation, 80.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
hugh@eoan:~$
```

This is vanilla Ubuntu, not Xubuntu but I believe snapd is present in a default Xubuntu installation.

---

### Post by mörgæs on 2020-01-10
A case of jump-to-conclusion from my side. I get the same output as yours.

Sorry for the detour.

---

### Post by pjstock on 2020-01-14
maybe I should back up one minute and ask whether my problem (with being able to access files from any location) has to do with permissions or something more global and not with specific applications.

Because I notice that other Snap apps that I have installed (like Kolourpaint) also cannot access a file from other than my Home location. (so I cannot open or import an image into Kolourpaint from my other HDDs. I have to copy the image over to a folder in Home and open it from there. And that is a bore.)

Before I go purging all my Snap installed apps, is there anything I can do to make them work more fluidly? to allow me to just attach a file from anywhere to an email for instance, or import an image for modification to Kolourpaint, but from anywhere.

Peter

---

### Post by Dennis N on 2020-01-14
> maybe I should back up one minute and ask whether my problem (with being able to access files from any location) has to do with permissions or something more global and not with specific applications.
Not file permissions, but depends on whether a specific interface is (or can be) connected.

Most users keep personal files in home folder, and that access is provided in snap applications that read/write your files through the home interface. You also get USB access via /media/<username> and access to /mnt if the snap is able to utilize the removable-media interface. 

You can check it removable-media access is available:

```
snap connections | grep removable-media
```

On this computer, only two snaps (chromium and firefox) have it:
```
dmn@Sydney-VM:~$ snap connections | grep removable-media
removable-media           chromium:removable-media                   :removable-media                 manual
removable-media           firefox:removable-media                    :removable-media                 manual

```
If the third column isn't blank, then it's connected. 'Manual' means it was manually connected (enabled) by the user.

---

### Post by TheFu on 2020-01-14
> **pjstock said:**
>  
Because I notice that other Snap apps that I have installed (like Kolourpaint) also cannot access a file from other than my Home location. (so I cannot open or import an image into Kolourpaint from my other HDDs. I have to copy the image over to a folder in Home and open it from there. And that is a bore.)

Before I go purging all my Snap installed apps, is there anything I can do to make them work more fluidly? to allow me to just attach a file from anywhere to an email for instance, or import an image for modification to Kolourpaint, but from anywhere.

By default, snaps only allow access to your HOME.
You can tell them to allow access to storage under /mnt/ or /media/ , but not everywhere, by using the 
```
$ snap connect chromium:removable-media
```
Just replace the program/snap name with the specific program (that is a snap package install) you want to have that access. I don't have the snap subsystem or I'd look up in the manpage exactly how to do the **snap connect **stuff. It will not help other programs that are not snap packages.

It is a failure/feature of snap confinement NOT to allow access elsewhere. Which is dependent on your view.

---

### Post by Dennis N on 2020-01-15
> You can tell them to allow access to storage under /mnt/ or /media/ , but not everywhere, by using the
```
$ snap connect chromium:removable-media
```
Just replace the program/snap name with the specific program (that is a snap package install) you want to have that access.


This only works if the snap has the necessary plug. Chromium has the plug, as output in post #25 shows, but for kolourpaint the connect command fails because it doesn't have that plug:

```
dmn@Tyana-vm:~$ snap connect kolourpaint:removable-media
error: snap "kolourpaint" has no plug named "removable-media"

``` 

Here are all supported interfaces in kolourpaint snap:
```
dmn@Tyana-vm:~$ snap connections kolourpaint
Interface                             Plug                               Slot                                                  Notes                                                         
content[kde-frameworks-5-core18-all]  kolourpaint:kde-frameworks-5-plug  kde-frameworks-5-core18:kde-frameworks-5-core18-slot  -                                                             
desktop                               kolourpaint:desktop                :desktop                                              -                                                             
desktop-legacy                        kolourpaint:desktop-legacy         :desktop-legacy                                       -                                                             
home                                  kolourpaint:home                   :home                                                 -                                                             
network                               kolourpaint:network                :network                                              -
network-bind                          kolourpaint:network-bind           :network-bind                                         -
opengl                                kolourpaint:opengl                 :opengl                                               -
pulseaudio                            kolourpaint:pulseaudio             :pulseaudio                                           -
unity7                                kolourpaint:unity7                 :unity7                                               -
x11                                   kolourpaint:x11                    :x11                                                  -

```

---

