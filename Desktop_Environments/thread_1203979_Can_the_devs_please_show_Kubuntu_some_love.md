---
title: "Can the devs please show Kubuntu some love?"
date: 2009-07-04
forum: Desktop Environments
---

### Post by AICollector on 2009-07-04
Ok all, I know Kubuntu isnt Canonicals main pritory...but I wish a bit more was done this time around. (9.04)

For instance; 

Inclusion of KPackageKit:

Has a lot of potential...and a lot of bugs, cannot resolve dependancies properly, refuses to display non graphical apps, removes-downloads-installs...all of those things need to be fixed and it feels like the devs just gave it a quick glance over and put it in the system. (Also, the fact that KPackageKit is set as 'trusted' by the KDE wallet is worrying, it allows KPackageKit to fully function without asking for permission.

KNetworkManager; This is borked, and will stay that way until 4.3 comes out (and even then, we could possibly have some issues). Feel's half baked, why werent alternate systems included on the disk? You know it's difficult to get ahold of the packages when you cant ruddy connect.


and what of the Ubuntu AppStore (or whatever it's name may be) will that be coming to Kubuntu? Will the system startup disk creator?

---

### Post by merlyn on 2009-07-04
I agree with you wholeheartedly.

I have since migrated across to Kubuntu for the first time as a fresh install.

Despite a few teething problems, that is me getting used to the different DE after using GNOME for years I love it.

It has now become my main desk top of choice.

I am however dissapointed with the implementation of Kpackagekit.

Search filtering is cumbersome.

Search results include, older packages than those installed, for some reason, often resulting in overly long lists.

There is always a discrepancy between the number of updates "notified" and those "listed" by kpackagekit.

It's quite clear that it is still a work in progress, and no doubt the wrinkles will be ironed out overtime.

It's also quite clear that it has a lot of promise.

But for me installing updates can result in an unstable system, and no I don't have any third party repositories set up, not yet anyway.

For example.

If an update notification is displayed in the system tray and I click on the notification icon to access kpackagekit to install them, my system will usually lock up once the packages are installed.

That is to say I cannot restart x, or access a terminal using <ctrl> <alt> <f...>, only a hard reboot works.

If however I access updates through System Tools > Add and Remove Programs > Software Updates the system never locks up.

Very odd behaviour as I've trialed other distros with KDE 4 ie Sidux, and Fedora 11 on my test laptop and there are no instabilites with kpackagekit.

Please give Kubuntu some love, care and polish

---

### Post by aged hippy on 2009-07-04
I've used Kpackagekit only once.... to install Synaptic. :biggrin: :popcorn:

---

### Post by AICollector on 2009-07-04
I want Synaptic for KDE :(

---

### Post by aged hippy on 2009-07-04
> **AICollector said:**
> I want Synaptic for KDE :(

Well if you're running Kubuntu 9.04 (either KDE 3.5 or KDE 4.x), install it with Kpackagekit. :)

---

### Post by AICollector on 2009-07-04
Correction; I want a native Synaptic :P

---

### Post by txcrackers on 2009-07-04
Yes, KPackageKit is a little on the brain-dead side. On the other hand, it's pretty new, so there are still some bugs to be worked out. Use synaptic in the mean time.

I've been using the new NetworkManagement plasma widget and, since they've fixed it up in 4.2.x, I must say I'm pretty impressed with it's ease of use. I don't think I even HAVE KNetworkManager installed on the netbook anymore...

---

### Post by stevie1989 on 2009-07-04
l totally argee with u AICollector! l prefer KDE over GNOME, and l was a hardcore Window user but haven't touched Vista(which is my fav MS OS, l have reasons) in weeks! But used GNOME awhile back, removed it farily quick and went back to MS. KDE is awesome! 

But it is buggy, network was a pain on the wireless card, and l can't get rid off Fuzzy Clock that won't let me get into it's settings (current 6:10 PM and it's saying ten past nine!?).
[ ]("http://ubuntuforums.org/member.php?u=580900")

---

### Post by AICollector on 2009-07-04
Removing KNetworkManager and replacing it with wicd:

KPackageKit: "Uninstall Knetworkmanager first."

I do so, and lo and behold, no internet connectiviy to download wicd!

Synaptic;

Downloading WICD, removing KNetworkManager, Installing WICD. Done.

Yay, internet! :D


Lets try another one;

Installing virtualbox 3.0 with KPackageKit.

"Sorry, there was an error."

That's ALL that is provided, no details, nothing. Just those words.


The error in this case was libcurl needed to be installed (which Synaptic would of done easily), I still feel that Kubuntu needs more work. I hope 9.10 indicates that, and they arent just copying everything from Ubuntu.

---

