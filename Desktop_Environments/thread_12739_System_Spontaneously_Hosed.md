---
title: "System Spontaneously Hosed"
date: 2005-01-26
forum: Desktop Environments
---

### Post by maus on 2005-01-26
I was using Ubuntu last night for my nightly routine of checking email, surfing the internet, and listening to music. Various and sundry things one does on a computer when they're not really working or playing. I was on my way to bed, and decided to burn a couple of talk radio mp3s to a CD-RW to listen to on my MP3-CD player while I slept. So I hit my Terminal window shortcut key so I can run a quick nautilus burn:///, and everything slows way, way down.

Now, it might have slowed down just prior to doing this, I don't know. I don't think this was the catalyst to the slowdown. Call it a hunch. Anyway, by the sound of my computer and the look of my HDD LED, it was accessing the hard drive for extremely short, regularly-spaced bursts, about four per second. And everything was SLOOOW.

So I Ctrl+Alt+F2-ed, and checked ps -A... nothing too weird. Huh. Well, maybe something nutty happened, and things needed a restart.

So I rebooted my workstation. As soon as it initialized X, BAM! things slowed way, way down. I waited about ten minutes for the machine to finish booting (a process that normally takes thirty seconds on a bad day), and killed all Gnome/X processes.

The terminal was pretty snappy, and at this point, I thought I had either an X problem or a hardware problem on my hands. 

So, what to do? Well, I decided to try and apt-get remove a bunch of my nvidia and XFree86 packages, then apt-get install them.

This is where things get nutty: after informing me what's going to happen (you know, the line that says '0 packages to be installed, 3 packages upgraded, etc'), it hangs for about five or so minutes. Then it errors out, giving me two errors that, while I cannot remember them verbatim, were something like:

- Perl may be unconfigured
and
- Cannot stat /bar/foo; access denied

So now Perl's hosed? On a side note, I did a find to try and see if I could locate my perl debian package. I always sudo my finds, since I don't like all of those 'Access Denied' messages cluttering up my output. Even under sudo, though, I got a few 'Access Denied' messages on some fairly esoteric folders.

So what could have cause my system to crap itself like this, and is there any way of fixing it short of a wipe and reinstall? I mean, I'm posting this from the LiveCD, and I can access my files and back them up if need be. I just don't want to have to re-setup and re-tweak everything the way I like it.

---

### Post by wayover13 on 2005-01-26
What does your sources.list file look like? I added the backports repositories recently, and my nicely-working Ubuntu system started to act flaky. I think the people involved in that backports project are not really competent enough to running such a project. If you've been apt-getting any backports stuff, or are maybe mixing other sorts of repositories, you may have introduced conflicts into the system. It's a guess, but might be worth considering. I'm not doing th backports thing anymore, regardless of how "stable" they say it is. If I need non-Ubuntu packages, I'll download debs from the main Debian repositories to my machine and resolve dependencies manually.

James

---

### Post by Buffalo Soldier on 2005-01-26
I've experienced that once. My Ubuntu froze and I had to hit the reset button. After that it took about 4 times longer to boot. And everything felt a bit slower.

Did a proper shutdown after that. Boot up again after a few minutes. Everything seems fine and been ok till now.

Maybe what I experience is totally unrelated to your problem. Just wanted to share.

---

### Post by maus on 2005-01-27
[QUOTE=wayover13]What does your sources.list file look like? I added the backports repositories recently, and my nicely-working Ubuntu system started to act flaky. I think the people involved in that backports project are not really competent enough to running such a project. If you've been apt-getting any backports stuff, or are maybe mixing other sorts of repositories, you may have introduced conflicts into the system. It's a guess, but might be worth considering. I'm not doing th backports thing anymore, regardless of how "stable" they say it is. If I need non-Ubuntu packages, I'll download debs from the main Debian repositories to my machine and resolve dependencies manually.

James[/QUOTE]

I do have the backports on. Assuming I remove them from sources.list, what can I do? Refresh and rebuild?

I'll also try a full shutdown and restart and see if that helps any, too.

---

### Post by maus on 2005-01-27
Okay, I think I know what the problem is, but not why, or how to fix it.

I'm getting a lot of 'access denied' on certain files and folders, even under sudo and in single user mode.

Oh, and here's the error message apt gives:

```

maus@lenin:~ $ sudo apt-get -f install

Reading Package Lists...
Building Dependency Tree...
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.8-plugin-apps gstreamer0.8-tools
Recommended packages:
  gstreamer0.8-plugins
The following NEW packages will be installed:
  gstreamer0.8-plugin-apps gstreamer0.8-tools
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 114kB/130kB of archives.
After unpacking 344kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com warty/main gstreamer0.8-tools 0.8.7-1ubuntu1 [114kB]
Fetched 114kB in 1s (112kB/s)
Selecting previously deselected package gstreamer0.8-tools.
(Reading database ... 111570 files and directories currently installed.)
Unpacking gstreamer0.8-tools (from .../gstreamer0.8-tools_0.8.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-plugin-apps.
Unpacking gstreamer0.8-plugin-apps (from .../gstreamer0.8-plugin-apps_0.8.5-1ubuntu3_i386.deb) ...
Setting up gstreamer0.8-tools (0.8.7-1ubuntu1) ...
Setting up gstreamer0.8-plugin-apps (0.8.5-1ubuntu3) ...
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting

```

This is getting increasingly frustrating.

---

### Post by nocturn on 2005-01-27
[QUOTE=maus]Okay, I think I know what the problem is, but not why, or how to fix it.

I'm getting a lot of 'access denied' on certain files and folders, even under sudo and in single user mode.

Oh, and here's the error message apt gives:

```

maus@lenin:~ $ sudo apt-get -f install

Reading Package Lists...
Building Dependency Tree...
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.8-plugin-apps gstreamer0.8-tools
Recommended packages:
  gstreamer0.8-plugins
The following NEW packages will be installed:
  gstreamer0.8-plugin-apps gstreamer0.8-tools
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 114kB/130kB of archives.
After unpacking 344kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com warty/main gstreamer0.8-tools 0.8.7-1ubuntu1 [114kB]
Fetched 114kB in 1s (112kB/s)
Selecting previously deselected package gstreamer0.8-tools.
(Reading database ... 111570 files and directories currently installed.)
Unpacking gstreamer0.8-tools (from .../gstreamer0.8-tools_0.8.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-plugin-apps.
Unpacking gstreamer0.8-plugin-apps (from .../gstreamer0.8-plugin-apps_0.8.5-1ubuntu3_i386.deb) ...
Setting up gstreamer0.8-tools (0.8.7-1ubuntu1) ...
Setting up gstreamer0.8-plugin-apps (0.8.5-1ubuntu3) ...
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting

```

This is getting increasingly frustrating.[/QUOTE]


It looks like you exerienced corruption on your harddisk.
What filesystem do you use?

Try booting from the livecd and run fsck on the root fs.

Also, on other systems with such problems I used rpm to verify packages, dpkg probably has a similar option).

---

### Post by maus on 2005-01-27
I'm using reiserfs for my root partition (hda3), and ext2 for my boot partition (hda2)

And, well, this is discouraging:

```

warty@ubuntu:~ $ sudo reiserfsck /dev/hda3
reiserfsck 3.6.17 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/hda3
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Thu Jan 27 21:47:46 2005
###########
Replaying journal..
Trans replayed: mountid 46, transid 850768, desc 5493, len 40, commit 5534, next trans offset 5517
Trans replayed: mountid 46, transid 850769, desc 5535, len 57, commit 5593, next trans offset 5576
Trans replayed: mountid 46, transid 850770, desc 5594, len 16, commit 5611, next trans offset 5594
Trans replayed: mountid 46, transid 850771, desc 5612, len 42, commit 5655, next trans offset 5638
Trans replayed: mountid 46, transid 850772, desc 5656, len 42, commit 5699, next trans offset 5682
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 5 transactions replayed
Checking internal tree../  1 (of   2)/ 15 (of 154)/ 69 (of 139)
The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (11436514): (Input/output error).

Aborted

```

What wacky moon language was that error message babelfished from, anyway?

At any rate, I'm not very familiar with the reiserfs tools; is there anything I can do that won't necessitate a new hard drive? I'm pretty sure I've had bad blocks for awhile on this thing; it's a four-year-old hard drive from the days when 80 GB was friggin' amazing.

EDIT: I found this: [http://namesys.com/bad-block-handling.html](http://namesys.com/bad-block-handling.html) and am currently following its advice

---

### Post by maus on 2005-01-28
Well, it looks like there lurks a bad block in my reiser system area. I guess I'll just fire up the ol' DVD Burner and evacuate the area.

Anyone know of a good way to extract personal settings for Gnome, Firefox, Thunderbird, etc?

---

### Post by fng on 2005-01-28
those are on the /home/your_user/.gnome, /home/your_user/.mozilla, /home/your_user/.mozilla-thunderbird, ...

look for directories starting with a . in your home dir (ls -a shows those.)

---

### Post by nocturn on 2005-01-28
[QUOTE=maus]Well, it looks like there lurks a bad block in my reiser system area. I guess I'll just fire up the ol' DVD Burner and evacuate the area.

Anyone know of a good way to extract personal settings for Gnome, Firefox, Thunderbird, etc?[/QUOTE]

If it is not to badly damaged, you can tar up your entire home directory.  That will save everyting you have.

---

