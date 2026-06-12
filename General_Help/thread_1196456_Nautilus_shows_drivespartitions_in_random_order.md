---
title: "Nautilus shows drives/partitions in random order"
date: 2009-06-25
forum: General Help
---

### Post by futz on 2009-06-25
My system (8.10 at present) has two 1TB, two 300GB and one 250GB drives divided up into the root/swap partitions and 13 archive partitions. I can't live with dynamic mounting (it's dangerous and unuseable), so I have my fstab set up like this:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=61e25586-524d-475c-a0be-034cb78ac09b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=40649613-d006-4ef0-bb73-96f6c09ae138 none            swap    sw              0       0
/dev/sda1	/media/sda1	ext3	defaults	0	2
/dev/sda2	/media/sda2	ext3	defaults	0	2
/dev/sda5	/media/sda5	ext3	defaults	0	2
/dev/sda6	/media/sda6	ext3	defaults	0	2
/dev/sda7	/media/sda7	ext3	defaults	0	2
/dev/sdb1	/media/sdb1	ext3	defaults	0	2
/dev/sdb2	/media/sdb2	ext3	defaults	0	2
/dev/sdb3	/media/sdb3	ext3	defaults	0	2
/dev/sdc1	/media/sdc1	ext3	defaults	0	2
/dev/sdd1	/media/sdd1	ext3	defaults	0	2
/dev/sdd2	/media/sdd2	ext3	defaults	0	2
/dev/sde1	/media/sde1	ext3	defaults	0	2
/dev/sde2	/media/sde2	ext3	defaults	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
That works just fine except for one thing that bugs me, and this only cropped up on Ubuntu 8.10 - earlier versions of Nautilus did it right - Nautilus displays the drives in random order in the Tree menu. They should be in alphabetical order. Random is horrible! I have to read through that list of 13 drives to find the one I want, which is invariably not where I'm looking, since my brain still thinks alphabetically. :grin:

There's probably a stupidly easy fix, right? Please tell me how!

EDIT: Just noticed that a root Nautilus displays the partitions in proper alpha sorted order. How strange!

---

### Post by capscrew on 2009-06-25
> There's probably a stupidly easy fix, right? Please tell me how!

Futz,

The OS assigns /dev/sdx designations in the order it discovers the partitions.  These can differ on each bootup.  The proper and most consistent ID is the UUID.  See the first entries in your fstab file as an example.

To find the UUID for all the partitions try this:```
sudo blkid
```

Edit your fstab file and use UUID for the partitions.

---

### Post by futz on 2009-06-25
> **capscrew said:**
> Futz,

The OS assigns /dev/sdx designations in the order it discovers the partitions.  These can differ on each bootup.  The proper and most consistent ID is the UUID.  See the first entries in your fstab file as an example.

To find the UUID for all the partitions try this:```
sudo blkid
```

Edit your fstab file and use UUID for the partitions.
That sure sounded like the cure, but it didn't change a thing. No change after a reboot.

Here's my new fstab in case you can spot something I've done wrong. All drives mount and work normally, but (non-root)Nautilus still displays them in (pseudo)random order.
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=61e25586-524d-475c-a0be-034cb78ac09b	/               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=40649613-d006-4ef0-bb73-96f6c09ae138	none            swap    sw              0       0
UUID=8eb325ef-7f1d-4d94-a1c3-c767bb4c72d0	/media/sda1	ext3	defaults	0	2
UUID=47b1f3fe-e274-4333-a75c-83bcd22d9575	/media/sda2	ext3	defaults	0	2
UUID=e7e489e6-cc4d-4210-852a-5326291a5f7d	/media/sda5	ext3	defaults	0	2
UUID=90b225c5-c88d-43a5-984f-17f8a81aa295	/media/sda6	ext3	defaults	0	2
UUID=ffea90a9-46e1-4141-816d-bf4556894c4f	/media/sda7	ext3	defaults	0	2
UUID=b47b5e50-ae8f-414d-8683-6e939e9cb914	/media/sdb1	ext3	defaults	0	2
UUID=6cef3002-1ca8-4b68-9b61-6bf14e86984e	/media/sdb2	ext3	defaults	0	2
UUID=e5c20118-f014-4446-b3e6-c83fef1cb82e	/media/sdb3	ext3	defaults	0	2
UUID=e6995054-8583-4790-9960-88ccb42aba4e	/media/sdc1	ext3	defaults	0	2
UUID=df5a6e21-e963-4fdc-b88c-6407ff2e973f	/media/sdd1	ext3	defaults	0	2
UUID=846f176d-0e1e-46fb-95a4-f8ccfda94ccb	/media/sdd2	ext3	defaults	0	2
UUID=72deafc2-6afd-4a86-9dfd-f7253b5541a4	/media/sde1	ext3	defaults	0	2
UUID=b942e07f-d807-4cdc-90b7-ce7bbecdcd5f	/media/sde2	ext3	defaults	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by capscrew on 2009-06-25
> That sure sounded like the cure, but it didn't change a thing. No change after a reboot.

Here's my new fstab in case you can spot something I've done wrong. All drives mount and work normally, but (non-root)Nautilus still displays them in (pseudo)random order.
Your fstab file looks fine.  I must have misunderstood you.  Can you explain what you mean by: "(non-root)Nautilus still displays them in (pseudo)random order".  A screen capture would help a lot.

---

### Post by futz on 2009-06-25
> **capscrew said:**
> Your fstab file looks fine.  I must have misunderstood you.  Can you explain what you mean by: "(non-root)Nautilus still displays them in (pseudo)random order".  A screen capture would help a lot.
OK, here's what the Nautilus tree view looks like. The order changes randomly every bootup:
[ATTACH]118983[/ATTACH]

And here is what a gksudo Nautilus tree view looks like. Nicely alphabetical. :grin: This is how it **should** look:
[ATTACH]118984[/ATTACH]

---

### Post by capscrew on 2009-06-25
Has it ever been in alphabetical order for the user (not root)?

Edit:  Please post this from the CLI: ```
df -h
```

---

### Post by futz on 2009-06-25
> **capscrew said:**
> Has it ever been in alphabetical order for the user (not root)?
It's been a while, but I remember versions prior to 8.10 being alphabetical. I may have skipped 8.04 though. Can't remember.

> Please post this from the CLI: ```
df -h
```
```
futz@xblade:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              46G   27G   17G  62% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  332K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  3.0M  1.7G   1% /dev
tmpfs                 1.7G  128K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda1              58G  3.5G   52G   7% /media/sda1
/dev/sda2             193G  175G  7.6G  96% /media/sda2
/dev/sda5             193G  180G  3.2G  99% /media/sda5
/dev/sda6             193G  172G   12G  94% /media/sda6
/dev/sda7             193G  146G   38G  80% /media/sda7
/dev/sdb1             309G  198G   95G  68% /media/sdb1
/dev/sdb2             309G  284G  8.9G  97% /media/sdb2
/dev/sdb3             309G   60G  233G  21% /media/sdb3
/dev/sdc1             276G   27G  235G  11% /media/sdc1
/dev/sdd1              97G   33G   60G  36% /media/sdd1
/dev/sdd2              97G   64G   28G  70% /media/sdd2
/dev/sde1              94G   12G   78G  13% /media/sde1
/dev/sde2             182G   58G  116G  34% /media/sde2

```

---

### Post by loomsen on 2009-06-25
Lol? Output from df -h? How could that help? :D

go to 
/usr/share/nautilus/ui/

everything regarding nautilus' UI is configured there...

[[img]http://www.ubuntu-pics.de/thumb/17209/screenshot_001_bYJih8.png[/img]](http://www.ubuntu-pics.de/bild/17209/screenshot_001_bYJih8.png)

I find it really annoying without Cut/Copy/Paste in the toolbar. 
Added another new tab item and a way to toggle hidden files, i'm just fine now :)
Pretty easy configurable... You probably have different sorting options (REMEMBER: graphical apps as ROOT can mess up a lot!) I use to have completely different skins for root and my normal $USER account. Compiz offers some protection with the titlebar info, but that's not enough at all imo. So, again, take care, I'd suggest you don't do anything at all as root.. If you consider you have to edit a file, make sure you make a backup of the original one (I usually do it in the same path by appending .original after I finished editing the file I copied to a temp folder, and there's nothing left to do)
So as root, only run cp and mv, and only cp/mv if it goes somewhere outside your $HOME. Just a couple of days ago a good friend came over and I had to fix thing up for him (5 or 6 .lock files owned by root he produced, wondering why his settings are locked down)
xml for the win ^^

---

### Post by dnairb on 2009-06-25
> **futz said:**
> OK, here's what the Nautilus tree view looks like. The order changes randomly every bootup.

Maybe Nautilus is listing by modification date, or something.

Try in Nautilus:

View --> Arrange items --> and select By Name

---

### Post by capscrew on 2009-06-25
I have no definite idea as to what is going on with Nautilus.  I see that the cli listing is not in alphabetical order either.

---

### Post by futz on 2009-06-25
> **loomsen said:**
> go to 
/usr/share/nautilus/ui/

everything regarding nautilus' UI is configured there...

Pretty easy configurable... You probably have different sorting options xml for the win
Ya... I'm pretty lost looking at XML. I program in assembly, C, Python, Perl and others, but I've never understood XML. There has to be another file somewhere that does something with the XML lists, right?

> I find it really annoying without Cut/Copy/Paste in the toolbar. 
Added another new tab item and a way to toggle hidden files, i'm just fine now :)
Heh. :grin: I'm a keyboard guy. Have some carpal tunnel pain from long years of mousing and typing, so I avoid the mouse whenever possible.

CTRL-H toggles hidden files. CTRL-C == Copy. CTRL-X == Cut. CTRL-V == Paste. Couldn't be simpler.

EDIT: Keyboard shortcuts - not all for Nautilus (CTRL-T and F5 work tho): CTRL-T == New tab. CTRL-S == Save. CTRL-O == Open. F5 or CTRL-R == Refresh. CTRL-L == Location bar. ALT-D or F6 or CTRL-L == Browser address bar. CTRL-N == New Nautilus or new browser or new file. CTRL-A == Select all. CTRL-S == (Nautilus) Select items matching. F2 == Rename. CTRL-K == Firefox search bar.

There are more. I don't know them all.

---

### Post by futz on 2009-06-25
> **dnairb said:**
> Maybe Nautilus is listing by modification date, or something.

Try in Nautilus:

View --> Arrange items --> and select By Name
That's actually in Edit/Preferences/Views, and it's always set to "By Name".

---

### Post by dnairb on 2009-06-25
> **futz said:**
> That's actually in Edit/Preferences/Views, and it's always set to "By Name".

The **global** setting is, yes. However one can have settings specific to each directory, under View -> Arrange Items.

---

### Post by futz on 2009-06-25
> **dnairb said:**
> The **global** setting is, yes. However one can have settings specific to each directory, under View -> Arrange Items.
Umm... There's no Arrange Items in my View menu. :tongue:

---

### Post by dnairb on 2009-06-25
> **futz said:**
> Umm... There's no Arrange Items in my View menu. :tongue:

Oh... I didn't realise that it was different in earlier versions.
If it's not under the right-click menu (in an empty space in the Nautilus window) then my help stops here, I'm afraid.

---

### Post by loomsen on 2009-06-25
gconf-editor -> apps -> nautilus -> list_view

[[img]http://www.ubuntu-pics.de/thumb/17221/screenshot_006_yZgd7r.png[/img]](http://www.ubuntu-pics.de/bild/17221/screenshot_006_yZgd7r.png)

Try...

---

### Post by futz on 2009-06-25
> **loomsen said:**
> gconf-editor -> apps -> nautilus -> list_view

Try...
Already been all through that. Nothing. Thanks for the suggestion.

[quote=dnairb]If it's not under the right-click menu (in an empty space in the Nautilus window) then my help stops here, I'm afraid.[/quote]
It isn't.

---

### Post by loomsen on 2009-06-25
Erm, what about labels...? 

As you say you have most of the partitions mounted for archieving purposes, shouldn't be a problem to unmount them, add a label to each one, and remount everything.

And my last guess. Go to computer:/// and chose your desired sorting method there. 
Then one probably would have to grep some files for sorting method/side panel or so.

---

### Post by futz on 2009-06-26
> **loomsen said:**
> Erm, what about labels...? 

As you say you have most of the partitions mounted for archieving purposes, shouldn't be a problem to unmount them, add a label to each one, and remount everything.
They're all labelled with the mount point name (sda2, sdc1, etc...). If you don't label, the OS autonames the partitions with their size. If you have multiple partitions with same size they end up with all the same names! Useless! :tongue: Labels are a must.

I don't think it does this anymore, but it used to autoname them as Disk1, Disk2, etc. Even more useless!

> And my last guess. Go to computer:/// and chose your desired sorting method there.
Then one probably would have to grep some files for sorting method/side panel or so.
I don't understand what you're getting at with that suggestion. Here's what computer:/// looks like:
[ATTACH]119005[/ATTACH]

---

### Post by mc4man on 2009-06-26
there have been several threads for quite some time about this and a somewhat similar behavior in the gnome-panel places and the r. click context menu.
All have had no working solution I've seen.

i guess you could take a look at the nautilus sources (in src), wouldn't hold out much hope though. (the random ordering is 'troublesome'

The volume labels shouldn't matter, appears you've already labeled them anyway.

---

### Post by futz on 2009-06-26
> **mc4man said:**
> there have been several threads for quite some time about this and a somewhat similar behavior in the gnome-panel places and the r. click context menu.
All have had no working solution I've seen.

i guess you could take a look at the nautilus sources (in src), wouldn't hold out much hope though. (the random ordering is 'troublesome'

The volume labels shouldn't matter, appears you've already labeled them anyway.
Ya, I'm assuming it's just a minor bug that'll be fixed in a later release. It's annoying but not a huge thing. 

I have a 9.04 box with four physical drives on one of the other ports of this KVM that I'm just doing the fstab on. Will report back if the bug exists in 9.04. It'll take a few minutes to get everything set up and reboot.

---

### Post by mc4man on 2009-06-26
> just a minor bug that'll be fixed in a later release

It may be something that doesn't get fixed. ( unless from happenstance

(plus it is ordered in the tree -> file system -> media, though obviously not exactly what  you're looking for

---

### Post by futz on 2009-06-26
> **mc4man said:**
> It may be something that doesn't get fixed. ( unless from happenstance
I think it should be fixed! Works perfect in a root Nautilus. So why not make a user Nautilus behave the same?

---

### Post by loomsen on 2009-06-26
> **futz said:**
> 
[ATTACH]119005[/ATTACH]

I meant sorting the items on the right side, but this doesn't work neither. Same behavior for me, can't even figure out any reasonable explanation which variable is used for sorting at all o.O

---

### Post by futz on 2009-06-26
> **futz said:**
> I have a 9.04 box with four physical drives on one of the other ports of this KVM that I'm just doing the fstab on. Will report back if the bug exists in 9.04. It'll take a few minutes to get everything set up and reboot.
Yup. Same thing in 9.04. Ah well... I won't die from it. Just bugs me is all.

---

### Post by futz on 2009-06-26
> **dnairb said:**
> Oh... I didn't realise that it was different in earlier versions.
If it's not under the right-click menu (in an empty space in the Nautilus window) then my help stops here, I'm afraid.
Hmm... There's no Arrange Items in the 9.04 Nautilus either. It's running v2.26.2 at present.

---

### Post by dnairb on 2009-06-26
nvm - was writing nonsense

---

