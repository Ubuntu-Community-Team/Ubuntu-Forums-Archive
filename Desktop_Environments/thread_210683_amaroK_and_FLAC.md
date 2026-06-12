---
title: "amaroK and FLAC"
date: 2006-07-07
forum: Desktop Environments
---

### Post by tool462rules on 2006-07-07
I use amaroK on Kubuntu, I have version 1.4.1 with KDE 3.5.3. My problem is that before I installed the extra xine codecs I had no problem playing FLAC files, but now that I do it says there is not audio channel.  But if I open them up in Kaffeine, they play no problem. MP3s play in both.  Is this a known problem, is it even a problem and can someone help?

---

### Post by Stephen Howard on 2006-07-07
Same problem here - flac was working fine until the update of a couple of days ago.

---

### Post by tool462rules on 2006-07-07
ok so it's not just me, anyone with a little more experience than I that can help?
I really like amarok (or however you capitalize it now) 1.4.1 the last.fm streams are nice (no personal radio though).
FLAC support is really important to me though.

---

### Post by asimon on 2006-07-07
The problem is the following. Amarok 1.4.1 checks now if the xine library supports the stream type before play. Because of a bug in Xine 1.1.1 xine reports that it doesn't support flac even through it does. Therefore amarok will not play flac.

There exists a patch for Xine 1.1.1 to fix this and Xine 1.1.2 will have it fixed too. Sadly neither is in Ubuntu so far.

See [bug 48612](https://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/48612) or the biased [blog from a Gentoo developer](http://farragut.flameeyes.is-a-geek.org/articles/2006/07/06/its-not-like-i-think-other-distribution-sucks-but).

---

### Post by Jucato on 2006-07-07
1. FLAC problems came with Amarok 1.4.1 only. AFAIK, it still works with Amarok 1.4.0

2. It's now officially Amarok :D
[http://amarok.kde.org/blog/archives/94-amaroK-is-now-Amarok.html](http://amarok.kde.org/blog/archives/94-amaroK-is-now-Amarok.html)

---

### Post by tool462rules on 2006-07-07
Do you think that since one of those will be in Edgy that they will maybe be backported in the future?
Which Xine version is 6.06 using and is there a patch for it?
Thanks for the notice though.

---

### Post by asimon on 2006-07-07
> **tool462rules said:**
> Do you think that since one of those will be in Edgy that they will maybe be backported in the future?
I hope so.

> **tool462rules said:**
> 
Which Xine version is 6.06 using and is there a patch for it?

Ubuntu 6.06 uses libxine version 1.1.1. The patch which is referenced in the bug report above could be used.

---

### Post by Jucato on 2006-07-07
well if it's just a patch, I hope either someone reports/reported it to the Kubuntu devs or that they make the patch available as soon as they can.

---

### Post by asimon on 2006-07-07
> **Fenyx said:**
> well if it's just a patch, I hope either someone reports/reported it to the Kubuntu devs or that they make the patch available as soon as they can.
Did you read this thread? ;-)
A bug was already filed yesterday in Malone and assigned to the respective maintainer.

---

### Post by Jucato on 2006-07-07
I read the thread, but didn't follow your links. I presumed that the bug report was filed in Gentoo. My bad. I guess I deserve that for not looking more closely. :(

---

### Post by Stephen Howard on 2006-07-08
There might be another option for those mere mortals like myself who are incapable of installing the patch (which I gather requires download of the 5+mb xine-lib src, patching it, figuring out build options (which don't appear to be documented in the src docs), successfully building it and then installing it).

I notice that if you highlight Amarok in Synaptic and then select *Package | Force Version* from the menu, there's an option to install Amarok 1.3.9 instead of the broken 1.4.1

Anyone tried that??

---

### Post by ivomans on 2006-07-09
> **Stephen Howard said:**
> I notice that if you highlight Amarok in Synaptic and then select *Package | Force Version* from the menu, there's an option to install Amarok 1.3.9 instead of the broken 1.4.1

Anyone tried that??

Didn't try it. But only want to tell you to use this "Force Version" if you don't have any other possibility. In this case there is a simple alternative way to get the same result: 
[LIST]
[*]remove the amarok141 repository from your sources.list
[*]remove amarok installation
[*]update repositories
[*]install amarok[/LIST]But I'm not sure if your collection will remain usable in the downgraded version. As said: I didn't try it.

---

### Post by tool462rules on 2006-07-09
i tried to do that and have had DB problems in all versions other than 1.4.1 since that.
I don't know if the only one that happens to.

---

### Post by Stephen Howard on 2006-07-10
> i tried to do that and have had DB problems in all versions other than 1.4.1 since that.

Which DB do you mean?  The apt package DB or Amarok's music DB?

---

### Post by tool462rules on 2006-07-10
amarok's DB.
it didn't give me an error message but there was nothing in the DB and I couldn't add anything.

---

### Post by mentok on 2006-07-13
Is it not possible to add the patched xine library to the Kubuntu repos so that it is not neccesary to download amarok? :confused:

Edit: Meant to write downgrade instead of download.:mad:

---

### Post by ivomans on 2006-07-13
Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

---

### Post by mentok on 2006-07-13
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

Thanks for the deb, but I use amd64 instead of i386, so I downloaded the source to libxine and the patch and patched it myself.

I've never built a package before so I doubt I followed all the conventions, but it seems to work (I can play FLAC files again). I can upload it if anyone wants it.

---

### Post by biggy_paul on 2006-07-15
Hi,

I just wanted to say thanks!! for the debs. I can now listen to my flac files again.

biggy_paul

---

### Post by herr-k on 2006-07-16
I hope the official patch will follow soon because my “music machine” which stores my whole collection encoded in flac is running on a PPC (with a decent soundcard of course).
Downgrading to 1.3.9 is not really an option for me because with no crossfading this version always cutted the last 1-2 seconds of a track and thus it made smooth reproduction impossible.
If the anger I already had with amarok would'nt be that great I'd patched it by myself ... maybe.
Please don't get me wrong. I apprecite the concept of amarok being not only a player but also a tool to organize your collection very much. This is a feature I really need. But it just seems it's still far from being mature, unfortunately. 
Sure, this is something I had to communicate at the amarok forums.

B.t.w this is the way I play flac files at the moment:

cd /flacdirectory
screen flac123 *.flac

Because my whole collection is properly numbered from “01 to nn” it works great. And “screen” makes possible to attach the process from every machine in my house.
But I still wish this will only be an interim condition not only because my girlfriend always rolling with her eyes when I say something like: “You have to protect a bracket with a backslash” (She uses xmms at the moment)  ;)

---

### Post by citizenkeith on 2006-07-17
ivomans,

THANK YOU! Worked like a charm. :)

---

### Post by TecnoVM64 on 2006-07-18
ivomans
You're my hero!!!, worked perfectly, thanks.

---

### Post by skyboy on 2006-07-27
worked like a charm here as well. 
Cheers !!

---

### Post by Spamuel on 2006-07-27
This worked like a charm, thanks.

Sam

---

### Post by atrus123 on 2006-07-27
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

Sweet!  The first patch did the trick.  Thanks for posting.

---

### Post by shamrock_uk on 2006-08-05
Thanks ivomans, much appreciated.

---

### Post by Baji on 2006-08-11
god bless you ivomans! :KS

---

### Post by isolationism on 2006-08-13
Could you post your AMD64 patched file(s) for me? I'm not accustomed to working with Ubuntu/Debian (I've used Gentoo almost exclusively for the past 3 years except for a touch of RHEL/CentOS server admin) so I'm pretty clueless about how to do fix this without manually compiling everything outside of the package manager context. Thanks.

---

### Post by mentok on 2006-08-15
It seems that the deb is too big to upload to the forum. PM me your email address and I can email it to you unless someone can suggest a better way to distribute this file...

libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb.bz2        2.7M

---

### Post by citizenkeith on 2006-08-15
> **mentok said:**
> It seems that the deb is too big to upload to the forum. PM me your email address and I can email it to you unless someone can suggest a better way to distribute this file...

libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb.bz2        2.7M

How about yousendit.com? At least for a temporary home...

---

### Post by mentok on 2006-08-18
> **citizenkeith said:**
> How about yousendit.com? At least for a temporary home...

Sound's good, just let me know where to send it.

---

### Post by citizenkeith on 2006-08-19
> **mentok said:**
> Sound's good, just let me know where to send it.

I usually send it to myself then post the link. That way, we can all partake. :)

---

### Post by mentok on 2006-08-19
> I usually send it to myself then post the link. That way, we can all partake.

I see, I wasn't sure how yousendit worked.

Here's the link.
[http://www.yousendit.com/transfer.php?action=download&ufid=1496982469A40759&rcpt=tjansse2@uwo.ca](http://www.yousendit.com/transfer.php?action=download&ufid=1496982469A40759&rcpt=tjansse2@uwo.ca)

Is there any word on when the patch will be in the official repository?

---

### Post by droogy on 2006-08-19
I get this error:

> dpkg: error processing libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb

SCRATH THAT... I was in the wrong directory.  It work fine!

---

### Post by dolny on 2006-08-20
Thanks a bunch mate! Now I can listen to my Katie Melua concert ;)

---

### Post by claypole on 2006-08-21
Thanks, this saved me a lot of hassle!!!

---

### Post by petersjm on 2006-08-21
> **claypole said:**
> Thanks, this saved me a lot of hassle!!!

Me too! Thanks for this! One thing, though... Not sure if it's related or not, but now I can't seem to scan through tracks? I could move the slider on the bottom and it would pick the song up where the slider was, but now when I move it, the track stops playing... Any clues?

---

### Post by reldruH on 2006-08-22
I installed the patch from ivomans and can play flacs now, but not oggFlacs. I was under the impression that anything that could play flac files would be able to play oggflac. I get the error message 'There is no audio channel!' Anybody have any ideas?

---

### Post by Jiilik on 2006-08-23
Thanks for the tip regarding the patch.  I've produced an amd64 package which I'm making available online:

[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb")
^^^ md5sum: 6d1abb121ad1d6c8284ada0538997220
[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/libxine-dev_1.1.1+ubuntu2-7.2_amd64.deb]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/libxine-dev_1.1.1+ubuntu2-7.2_amd64.deb")
^^^ md5sum: 5b96d691581b5a927358177561e68ab2

You can install these using dpkg -i which just replaces the existing packages.

---

If you want to build this for other platforms, or are interested in how I did this, grab the following files and follow the instructions below:

[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2.orig.tar.gz]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2.orig.tar.gz")
^^^ md5sum: 5d0f3988e4d95f6af6f3caf2130ee992 (same as original from packages.ubuntu.com)
[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2-7.2.diff.gz]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2-7.2.diff.gz")
^^^ md5sum: c19927f3c169632341348d970cf51697 (includes flac fix and all other official ubuntu packages)
[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2-7.2.dsc]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/xine-lib_1.1.1+ubuntu2-7.2.dsc")
^^^ md5sum: a4c64100c227cb0041bcb3bbda87e875 (updated dsc files for patch, signed by me)

Once downloaded, put these files in a folder someplace and run the following commands:
```

dpkg-source -x xine-lib_1.1.1+ubuntu2-7.2.dsc
cd xine-lib-1.1.1+ubuntu2
debuild -i -us -uc -b

```
*note: it'll ask you for your pgp passphrase... if you don't have one, don't worry too much since it's only used for signing the files... if you're building for use on your system only, I wouldn't worry about it.

[INDENT]optionally you can use the official packages from packages.ubuntu.com, but then you need to apply the patch yourself... grab the patch here:
[http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/flac-fix.patch]("http://tblog.ath.cx/~troy/ubuntu/xine-lib+flac-fix-for-amarok/flac-fix.patch")
^^^ md5sum: 0e49af0b79d03d3431979efd1959d73c
Apply this patch with ```
patch -p1 < flac-fix.patch
``` to the sources before running debuild[/INDENT]

---

### Post by citizenkeith on 2006-08-24
Has anybody gotten the new beta to work yet?

---

### Post by crxyem on 2006-08-24
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 


[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]


Thanks very much, the 1st patch worked for me.

---

### Post by dlepiane on 2006-09-01
Works good, thx!

---

### Post by tjmcwiz on 2006-09-02
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

Thanks for the patch --- it corrected the problem I was experiencing with my FLAC files as well

---

### Post by citizenkeith on 2006-09-02
If you're still having problems playing certain FLAC files, try this: Run EasyTag and rewrtite the ID3 tags for those FLAC files.

I recently had some FLAC files which I created with Grip and FLAC. If I were to check the file properties in Gnome, it would display "MP3" even though it was a FLAC file. Something happened when the MIME type was written to disc. Anyway, changing the ID3 tag fixed it, and Amarok was able to play the file again.

---

### Post by happyisland on 2006-09-04
Hi,
I'm an Ubuntu noobie having the same problem playing flac files in what has become my favorite music player, Amarok. I run the 64 bit flavor of Ubuntu and I guess I need to install the packages linked in post 39 of this thread. Thing is, I'm such a beginner I don't really know how to do that. Does anyone out there have the patience to walk me through it?
Thanks in advance to a great community.

---

### Post by BIGtrouble77 on 2006-09-05
happy island,
you should just have to type:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb
```
In the command prompt.  Just make sure you're in the directory that holds that file.

With that said, the file will not install for me.  Here's the error:
```
(Reading database ... 124076 files and directories currently installed.)
Preparing to replace libxine-main1 1.1.1+ubuntu2-7.2 (using libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb) ...
Unpacking replacement libxine-main1 ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/xine/plugins/1.1.1/xineplug_inp_vcd.so')
Errors were encountered while processing:
 libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb

```
I've never had an error like this before.

EDIT: I tried installing it through the package manager and it worked perfectly.  Amarok work fine now with flac.

---

### Post by happyisland on 2006-09-05
Ok, for some reason when I tried the command line approach it didn't work. Newbie approach #2: I double-clicked the downloaded .deb file. And viola! I'm listening to flac right now. Thanks all!

---

### Post by hogweed on 2006-09-08
> **ivomans said:**
> 

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

Thanks! Works fine with me for Amarok 1.4.3.........:-D

---

### Post by tescov_1999 on 2006-09-08
Just want to thank you for the patch, I have mixed formats and i was starting to go nuts having Amarok lock up when it hit a flac file....thanks again


_rob

---

### Post by brandon_r87 on 2006-09-08
Can't install the libxine-main amd64 package by Jiilik.  When I try to install it, I get this,

```

dpkg-deb: `/home/brandon/Desktop/libxine-main1_.1.1+ubuntu2-7.2_amd64.deb' is not a debian format archive
dpkg: error processing /home/brandon/Desktop/lixine-main1_1.1.1+ubuntu2-&.2_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/brandon/Desktop/libxine-main1_.1.1+ubuntu2-7.2_amd64.deb
Press <enter> to exit...

```

](*,)

---

### Post by bartek on 2006-09-10
I think this patch might have messed up sound playback in Firefox (ie no sound in youtube videos)?

---

### Post by ivomans on 2006-09-11
To all the posters of the 'thank you' messages: I appreciate that you let me know it's working. Glad I could help.

> **bartek said:**
> I think this patch might have messed up sound playback in Firefox (ie no sound in youtube videos)?

I just tried a few videos on the frontpage of youtube: no problem in my Firefox.
The patch was downloaded 330 times now and you're the first experiencing a problem.  Are you sure it was working before the patch? If you reinstall the original version is the problem solved again? Can you give any specifics on your system and with which video exactly you've got the problem, so that we can compare?

---

### Post by mentok on 2006-09-11
> **bartek said:**
> I think this patch might have messed up sound playback in Firefox (ie no sound in youtube videos)?

I've noticed that same problem intermittently. Sometimes sound works, sometimes it doesn't. I'm not sure exactly what causes it but I know a quick and dirty workaround

start firefox with the command:
```
aoss firefox
```

you may need to install the 'alsa-oss' package.

---

### Post by Phil Urich on 2006-09-12
Thanks a million for the patch! . . . but, I'm having a problem now, and I KNOW that it's only cropped up since the patch since immediately (a few minutes) before I installed the patch it was working, the "it" being transferring to my portable audio player.

Bascially, say I'm trying to transfer a track over now.  It goes, for example, like this with two of those error popups:

> Media Device: Reading tags from file:///media/sdc1/Abandoned Pools - Armed To The Teeth/01 Lethal Killers failed
> Failed to copy track to media device: /media/hdb1/Media/Music/Abandoned Pools - 2005 - Armed To The Teeth (advance)-rns/01-abandoned_pools-lethal_killers.mp3

I can easily copy files manually, so it's not even much of a deal except a bit for podcasts.  Really just a nitpick, and if no one has any ideas on fixing that then so be it.

My other issue, though, is that the gstreamer and arts engines for amarok are still stuck on dependency for the older version, so I can't check and see if it'd work with those ones . . . I suppose I should have known better than to try to use the bleeding edge version of a program :( but I do really like every new version of amarok even more so I'm kinda addicted to upgrading it whenever the chance comes.

---

### Post by pneaveill on 2006-09-12
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]
Wow!! It worked the first time!! Thanks so much for this thing and God bless you for taking the risk, time, effort and all that!!

---

### Post by ronmarley1 on 2006-09-14
Thanks for the patch!  I'm back in business!

---

### Post by brandon_r87 on 2006-09-14
Mentok, could I get your amd64 patches?  I couldn't download them from the yousendit link and Jilik's patches won't install for me.

---

### Post by mentok on 2006-09-15
> **brandon_r87 said:**
> Mentok, could I get your amd64 patches?  I couldn't download them from the yousendit link and Jilik's patches won't install for me.

I've put it up on yousendit again at

[http://download.yousendit.com/12FB09DD786F79BA]("http://download.yousendit.com/12FB09DD786F79BA")

If anyone knows a more permanent place I can put this, please let me know.

---

### Post by ivomans on 2006-09-16
> **mentok said:**
> 
If anyone knows a more permanent place I can put this, please let me know.

I just copied your file to my site, where I'm already hosting the i386 files. Now your file is available from this link:
    [libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb")

---

### Post by neologisma on 2006-09-16
Ivomans,

I did your patch trick and amarok is working fine now. The problem is that the Synaptic manager keeps saying that  libxine-dev is broken/crashed and I can't make any downloads if I don't fix it. What do I do to correct it?
(I use Kubuntu 6.06 and newbbie to this stuff).

Thanx! :cool: 

> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]

---

### Post by cptjaben on 2006-09-16
Thanks for the help, worked perfectly

---

### Post by ivomans on 2006-09-17
> **neologisma said:**
> I did your patch trick and amarok is working fine now. The problem is that the Synaptic manager keeps saying that  libxine-dev is broken/crashed and I can't make any downloads if I don't fix it. What do I do to correct it?
(I use Kubuntu 6.06 and newbbie to this stuff).


Is it possible you only installed the libxine-main patch? Download also the 2nd link from my mail and execute the command:
```
sudo dpkg -i libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb
```

---

### Post by neologisma on 2006-09-17
#-o  Ooops... You're right. Thanks!

---

### Post by blip on 2006-09-18
Scweet!  The patches worked for me.... Thanks for saving me the trouble of doing it manually.

God I love the Ubuntu community!

---

### Post by xwm on 2006-09-18
Hey,


 Can anyone help me?


I've installed amarok but I can't listen to any of my MP3 music... I've already installed gstreamer-08.mad......

The problem is that when I press play button all my file music are played in a second.....

       What's going on?????!!!:confused: :( :frown:

---

### Post by citizenkeith on 2006-09-18
> **xwm said:**
> Hey,


 Can anyone help me?


I've installed amarok but I can't listen to any of my MP3 music... I've already installed gstreamer-08.mad......

The problem is that when I press play button all my file music are played in a second.....

       What's going on?????!!!:confused: :( :frown:

You need mp3 codecs installed, most likely. Try Automatix which will give you everything you need. :)

---

### Post by xwm on 2006-09-19
Thank you citizenkeith, I've tried Automatix and it went great....:p :razz:

---

### Post by isolationism on 2006-09-19
This is just another reply to say "Thanks" and that I finally have Amarok playing FLAC on AMD64 again (hasn't worked since I switched from Gentoo to Ubuntu). Thanks mentok, ivormans et al.

---

### Post by symbol on 2006-09-28
Thanks a lot,and I put mentok's file on my site,everybody can download it

[http://www.iwxm.net/deb/libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb](http://www.iwxm.net/deb/libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb)

---

### Post by jeroen2 on 2006-10-05
libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb worked like a charm for me. Thanks so much!

However, ubuntu has now made 2-7.3 available in their repo's, so I get the update manager al the time mentioning this. Can this path also be applied to 2-7.3? 

Btw, any good guides around on packaging and patching? I already know how build rpm's but would love to contribute to the kubuntu community.

~Jeroen

---

### Post by dukeku on 2006-10-05
libxine-main1 1.1.1+ubuntu2-7.3 broke flac support again for me :(

---

### Post by ivomans on 2006-10-05
I just uploaded the new released version with the old patch. Works for me.

Available at:
[LIST=1][*][libxine-main1_1.1.1+ubuntu2-7.3+patch1_i386.deb]("http://www.xs4all.nl/~manik/download/libxine-main1_1.1.1+ubuntu2-7.3+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.3+patch1_i386.deb]("http://www.xs4all.nl/~manik/download/libxine-dev_1.1.1+ubuntu2-7.3+patch1_i386.deb")
[/LIST]

---

### Post by PigCorpse on 2006-10-05
YEAH!

We love you! In a computer nerd way!

---

### Post by dukeku on 2006-10-05
Right as I finished mine! Think of it as a mirror ;)

[http://oool.org/ubuntu/libxine-dev_1.1.1+ubuntu2-7.3-patch0_i386.deb](http://oool.org/ubuntu/libxine-dev_1.1.1+ubuntu2-7.3-patch0_i386.deb)
[http://oool.org/ubuntu/libxine-main1_1.1.1+ubuntu2-7.3-patch0_i386.deb](http://oool.org/ubuntu/libxine-main1_1.1.1+ubuntu2-7.3-patch0_i386.deb)

---

### Post by PigCorpse on 2006-10-05
How come ivomans' is patch1, yet dukeku's is patch0?

---

### Post by ivomans on 2006-10-06
> **PigCorpse said:**
> How come ivomans' is patch1, yet dukeku's is patch0?
It's just a name chosen. No further meaning behind it. Most important with the naming is that a possible new securityrelease will override the patched version.

---

### Post by PigCorpse on 2006-10-06
So packages overwrite others based on their filenames?

How did you patch them? Share the wealth! :D

---

### Post by imaca on 2006-10-06
I have same problem.
Tried patching again but reports "newer version already installed"
Can't go back to old version either - end up with broken amarok package

---

### Post by Rhapsody on 2006-10-06
> **ivomans said:**
> It's just a name chosen. No further meaning behind it. Most important with the naming is that a possible new securityrelease will override the patched version.
It seems that's just what a security update did on my system. Guess I'll have to keep on top of these patches until there's an official fix in the repositories.

---

### Post by happyisland on 2006-10-06
Anybody do a amd64 patch yet? Pretty please?

---

### Post by happyisland on 2006-10-06
also, does anyone have a noob-friendly explanation as to why libxine wouldn't allow FLAC to work? I thought FLAC was the most badass OSS codec, and that's why I switched to it. Strange that it doesn't *just work*.

---

### Post by cptjaben on 2006-10-07
Thanks for the help.

---

### Post by jeroen2 on 2006-10-07
> **happyisland said:**
> also, does anyone have a noob-friendly explanation as to why libxine wouldn't allow FLAC to work? I thought FLAC was the most badass OSS codec, and that's why I switched to it. Strange that it doesn't *just work*.

As noob-friendly as I can:

Amarok itself can't play FLAC, so "under the hood" it uses another program: libxine. Libxine 1.1.1 has an error: it _can_ play Flac, but when _asked_ says it can't. Amarok, instead of saying to libxine "yo, play this flac for me" first asks: "dude, are you capable of playing flac?". Libxine says "nope sorry" and Amarok doesn't try any further.

Hope that covers it.

~Jeroen

---

### Post by happyisland on 2006-10-07
Thanks for the explanation Jeroen. Why does this problem persist, even in updated versions of libxine and Amarok? Also, is there any newby-friendly way to make this work again? Last time I downloaded a patched version of libxine that someone else had made...

---

### Post by PigCorpse on 2006-10-08
How come ivomans' has a different file size than dukeku's?

---

### Post by dukeku on 2006-10-09
> **happyisland said:**
> Thanks for the explanation Jeroen. Why does this problem persist, even in updated versions of libxine and Amarok? Also, is there any newby-friendly way to make this work again? Last time I downloaded a patched version of libxine that someone else had made...

A slightly more complex explanation - xine needs to report that XINE_STREAM_INFO_HAS_AUDIO is true, but in the current version it reports that it doesn't, making amarok think that there's no audio stream to play. I don't know why it's not currently fixed, but apparently it's going to be fixed for Edgy.

> **PigCorpse said:**
> How come ivomans' has a different file size than dukeku's?

He might have built the package with debuild or dpkg-buildpackage, I used fakeroot. They both accomplish the same thing :D

---

### Post by hoe on 2006-10-09
I see 1.4.3-1 in the Debian repository. Wonder if this will solve the problem:

[http://packages.debian.org/unstable/kde/amarok-xine](http://packages.debian.org/unstable/kde/amarok-xine)

[http://packages.debian.org/unstable/kde/amarok](http://packages.debian.org/unstable/kde/amarok)

Wayne

---

### Post by hvidgaard on 2006-10-10
As far as I have understood, the problem is not within Amarok (but an update could do it) but the Xine engine...

I have put the fixed files at my website :)

[xine-flac-update]("http://hvidgaard.dk/download/xine-flac-update/")

edit: the link has changed :)

And if I am missing some patches or new arrive, please pm me so I can upload them :cool:

---

### Post by happyisland on 2006-10-10
hivdgaard - thank you so much for the patches! You are my hero - I am able to listen to my music again!

---

### Post by hvidgaard on 2006-10-11
> **happyisland said:**
> hivdgaard - thank you so much for the patches! You are my hero - I am able to listen to my music again!

No problem :) But I'm only hosting, thank the guys that actually made them ;)

---

### Post by happyisland on 2006-10-11
Cool - who did make them? You all made my day!

---

### Post by thojoh on 2006-10-14
thanks a lot!   Problem solved here as well!   :D

---

### Post by dearephesus64 on 2006-10-15
Just adding my thanks in there, too.  It worked fine.

I know nothing about installing deb packages though- will any of those patches interfere with Adept updating libxine when a new version is added to the repository in the future?

---

### Post by ivomans on 2006-10-15
> **dearephesus64 said:**
> I know nothing about installing deb packages though- will any of those patches interfere with Adept updating libxine when a new version is added to the repository in the future?

This will not interfere with future updates. When a new update is released it will overwrite the patched version. Hopefully the patch is included in the official version by then. If not the FLAC problem will return with that upgrade, but in that case you could expect a new patch in this thread shortly after.

---

### Post by isagani on 2006-10-17
This is great! Thanks.. it worked like a charm. :)

---

### Post by n1x0r on 2006-10-20
magnificent! thx especially for the amd64 deb!  anyone know why this remedy isn't in w/ the official packages?

---

### Post by Sweet Spot on 2006-10-25
Just another THANK YOU< THANK YOU< THANK YOU !  Totally right 1 :mrgreen:

Doug

---

### Post by isolationism on 2006-10-26
Ivormans,
You are indeed correct: In fact, for some reason I don't understand, Ubuntu wants to update the package immediately after I install the patched version (even though the verson numbers are the same for both). I really don't want to upgrade to the 'Official' package until flac support is built in, but I don't want the package to show up in the "updates" dialog either (because I just know I'll accidentally install overtop of my working libxine again as I did recently).

You know know of any equivalent to Gentoo's package.mask for Ubuntu? Something that I can tell the OS, "ignore updates for this package, the one I have is just fine until I explicitly say otherwise"?

---

### Post by ivomans on 2006-10-26
> **isolationism said:**
> You know know of any equivalent to Gentoo's package.mask for Ubuntu? Something that I can tell the OS, "ignore updates for this package, the one I have is just fine until I explicitly say otherwise"?

I trust the 'official' package is updated for some good security reason, so I don't advice you to neglect these updates. This thread has proven a fast new patch will be available shortly after an official update.

But to answer the question: yes, there is a way to do so. Check out the possibilities of the file /etc/apt/preferences. I've got in this file a setting to prevent update of my jabber server. That looks like this:
```
Package: jabber
Pin: version 1.4.3-3
Pin-Priority: 1001
```
It should be quite easy to figure out the setting for libxine.

---

### Post by ivomans on 2006-10-26
Tonight I upgraded one Kubuntu system to Edgy. 
This also installed the newer libxine 1.1.2.

I'm now listening to a flac file in Amarok with the official libxine!

---

### Post by hvidgaard on 2006-10-27
> **isolationism said:**
> Ivormans,
You are indeed correct: In fact, for some reason I don't understand, Ubuntu wants to update the package immediately after I install the patched version (even though the verson numbers are the same for both). I really don't want to upgrade to the 'Official' package until flac support is built in, but I don't want the package to show up in the "updates" dialog either (because I just know I'll accidentally install overtop of my working libxine again as I did recently).

You know know of any equivalent to Gentoo's package.mask for Ubuntu? Something that I can tell the OS, "ignore updates for this package, the one I have is just fine until I explicitly say otherwise"?


You can use 'Force version' in Synaptic, but don't forget it :) or else, upgrade to Edgy ;)

---

### Post by henriquemaia on 2006-10-31
> **hvidgaard said:**
> No problem :) But I'm only hosting, thank the guys that actually made them ;)

Thanks for hosting the files. This also helped me in getting amarok to play my flac again.

---

### Post by petersjm on 2006-11-04
Bummer. Is there an uninstall for the patch provided earlier in this thread? Since I installed it, Ubuntu is "holding back" about 15 or 20 updates because of it -- or at least I think it 's because of this; it happened about the same time. When I try to uninstall the patch, it wants to remove Amarok and Totem too...

---

### Post by ChrisNiemy on 2006-11-06
EDIT: Problem solved! The problem was only with flacs made with Grip. There some parameters there in the encoding section which made the troubles. when i manually converted a wav to a flac with /usr/bin/flac in command line it works perfectly with all xine apps and amarok.
though the with grip created flacs only work with gstreamer is strange.
however, you just have to adjust the parameters in grips enconding section.

UPDATE: The settings in Grip weren't wrong by default, I guess.
A rm ~/.grip and rm ~/.xine solved the problem completely. :D
Maybe myself messed up the settings in Grip. 

I guess the error was, that I had uncheck "add IDv3 Tags only to files ending with .mp3" That was the problem. FLAC uses FLAC Vorbis Tags, I guess. So it's Flac Vorbis Tag vs. IDv3 Tag problem and that xine is more accurate with that.

Here's a solution how to create working FLAC tags with Grip:
[http://sourceforge.net/mailarchive/forum.php?thread_id=1634089&forum_id=5443](http://sourceforge.net/mailarchive/forum.php?thread_id=1634089&forum_id=5443)

[SIZE="1"]Hi there!

Can anyone play flac now under edgy with Amarok and Xine out-of-the-box?
Have all packages installed, not working. Same behaviour as with the bug under dapper. :(

Can someone reproduce playing (or not playing) FLAC files with amarok (1.4.3) and xine under egdy? Thanks,
Chris


PS: Tried also from the edgy live cd and installed the packages. flac generally works fine, but xine apps like amarok refuses it. There is NO error message, because the codec for xine (libxine-extracodecs) is installed.
a pity that the xine package was not fixed for edgy. :(


How about a new patched deb for edgy? :)

Greets, Chris


PPS: in the output of the command xine-config is an interesting line
> (...)
[ good ] plugin directory /usr/lib/xine/plugins/1.1.2 exists.
***[ good ] found unknown plugin: xineplug_flac.so***
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
(...)
[/SIZE]

---

### Post by casfindad on 2006-11-11
> **tool462rules said:**
> I use amaroK on Kubuntu, I have version 1.4.1 with KDE 3.5.3. My problem is that before I installed the extra xine codecs I had no problem playing FLAC files, but now that I do it says there is not audio channel.  But if I open them up in Kaffeine, they play no problem. MP3s play in both.  Is this a known problem, is it even a problem and can someone help?

I had the same problem with Amarok 1.4.4. For those of you (like me) who don't know how to install the patch contained in the bug report, there is an alternate deb package patch that is very easy easy to install. The patch and installation instructions are available [here]("http://element14.wordpress.com/2006/09/28/play-flac-files-in-amarok-on-ubuntu/").
Worked for me first time. Good luck!

casfindad

---

### Post by khaije1 on 2006-11-11
It seems possible that these recent problems with xine (amarok, gxine, & many other players) is because of a change in the way that files are checked by xine before being played. 

(this is a follow up to [Chris's previous post]("http://ubuntuforums.org/showpost.php?p=1720787&postcount=104") investigating the significance of id3 vs vorbis tagging on this problem)
 
Could it be xine detects audio type based on the tag? I suspect that xine fails because it is trying to play a flac file thinking it is an mp3. I've read elsewhere that xine/amarok recently improved it's audio type detection, and that this should help with crashes because invalid files will be refused by xine lessening the chances they will cause a crash. 

i suspect->
1. amarok picks the file 
2. amarok feeds the info (mrl, etc) to xine
2. xine checks the type and prepares to play it
3. xine rejects the "open new audio channels for this file" request due to conflicting/incompatible info
4. amarok reports that it cannot open audio channel
(this is a guess, anyone know for certain?)
This makes sense since this didn't use to be a problem, yet has persisted between multiple versions of xine. It is because stricter type-checking is actually an important improvment!

here is a test that i tried from my laptop in order to demonstrate the issue (more conclusive tests to come later)

```
n1x0r@callisto:~/tmp/test$ file testing.flac 
testing.flac: MP3 file with ID3 version 2.3.0 tag
n1x0r@callisto:~/tmp/test$ # xine won't play
n1x0r@callisto:~/tmp/test$ id3v2 --delete-all testing.flac 
Stripping id3 tag in "testing.flac"...id3v1 and v2 stripped.
n1x0r@callisto:~/tmp/test$ file testing.flac 
testing.flac: FLAC audio bitstream data, 16 bit, stereo, 44.1 kHz, 8042076 samples
n1x0r@callisto:~/tmp/test$ # will play fine in xine now!!! :-)

```

Is xine's detection based on something similar to the 'file' command? If so, it would explain why testing.flac is detected incorrectly (at first) as a result of the id3 tag headers in the file. Consequently removing the id3 tag completely allows 'file' to properly id it, and for xine to properly play it.
In fact, re-adding the id3 tags recreates the original problem! 

Which seems strange until you read this...
[what tags can flac support?]("http://flac.sourceforge.net/faq.html#general__tagging")

But when i encoded my flac's i didn't ask for id3!!!
Or at least i didn't think so... In my case this is due to foolishly checking an unnecessary option in Grip that explicity asked "add id3 to non-mp3 files?" (exactly the same as ChrisNiemy)

if i had to guess i would say that because the metadata for mp3's and flac's is written at the head of the file it is what determines the type when using tools like file, which examine the head of a file for an identifier. This is why the result is so changeable even though it seems like it shouldn't be.

This also explains why some flac's work and others do not! 


**more testing:**
Could this be related to the xine-extracodecs package? Some people have reported only having problems after installing it...

**ideal solution:**
(1) fix xine-- xine will engineer support for tagging flac files with id3.
or
(2) fix files-- the trick now will be to find a strong method (script or gui) for safely testing this on a system, and then (after confirmation) converting the id3 tags to flac/vorbis tags (which i think are the same thing) without losing any data.

I'm going to go with option (2). For all i know there is a good reason that (1) hasn't been done yet, and it is probably a more tidy solution anyway.

I'll start looking into this tonight and post my results. Any and all assistance is appreciated. 

NB: thanks to loutrine and ChrisNiemy in particular. Though Chris already pointed alot of this out, I just wanted to add a little and confirm/clarify for those who may benefit from it.

Cheers,

---

### Post by beastly on 2006-11-16
Thanks guys for the patches, but I'm still having problems with a fully updated x86-64 Edgy system. I tried running the latest patch but it won't let me install the patch (at least, not without forcing it) because I have a newer version of libxine:

```
~>sudo dpkg-query -l "libxine*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  libxine-extracodecs          1.1.2-0ubuntu2               the xine video/media player library, binary files
ii  libxine-main1                1.1.2+repacked1-0ubuntu3     the xine video/media player library, transitional package
ii  libxine1                     1.1.2+repacked1-0ubuntu3     the xine video/media player library, binary files
un  libxine1c2                   <none>                       (no description available)
ii  libxinerama-dev              1.0.1-4build1                X11 Xinerama extension library (development headers)
ii  libxinerama1                 1.0.1-4build1                X11 Xinerama extension library

```

Here is the error I encountered:

```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb
Password:
dpkg - warning: downgrading libxine-main1 from 1.1.2+repacked1-0ubuntu3 to 1.1.1+ubuntu2-7.3.
dpkg: considering removing libxine1 in favour of libxine-main1 ...
dpkg: no, cannot proceed with removal of libxine1 (--auto-deconfigure will help):
 totem-xine depends on libxine1 (>= 1.1.2-5)
  libxine1 is to be removed.
dpkg: regarding libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb containing libxine-main1:
 libxine-main1 conflicts with libxine1
  libxine1 (version 1.1.2+repacked1-0ubuntu3) is installed.
dpkg: error processing libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb (--install):
 conflicting packages - not installing libxine-main1
Errors were encountered while processing:
 libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb

```

Any ideas? Should I downgrade libxine to 1.1.1 then apply the patch? I am getting a strange effect, in that I can load a FLAC file directly into Amarok and it will play, but when I add my folders containing my FLAC files to the collection Amarok will spend some time scanning the folders (so I expect it's examining all the FLAC files) but when it completes none of them have been added to the collection. Is this what other people experience?

Thanks for any help.

---

### Post by hvidgaard on 2006-11-18
That is indeed strange... I'm running a fully updated Edgy x86-64 system, and I have no problem at all. Try to uninstall Amarok completly (including all conf files) and reinstall it.

---

### Post by seamus7 on 2006-11-19
I am on Ubuntu Edgy and installed Amarok 1.4.4. After I enabled libxine-extracodecs my flac files played and my cue sheets displayed. :)

[https://launchpad.net/distros/ubuntu/+source/amarok/+bug/64075](https://launchpad.net/distros/ubuntu/+source/amarok/+bug/64075)

---

### Post by steevc on 2006-11-23
I've just started converting CDs to FLAC and have hit some issues. I rip them in Konqueror. When I play back in Amarok (1.4.3 on Edgy) it cuts off the last few seconds of each track, but otherwise sounds fine. The other issues are that I can't go forward in the track by moving the slider and I have had some crashes and lock-ups. The tracks play fine in VLC.

---

### Post by Rhapsody on 2006-12-05
A new security update for libxine-main 1.1.1 has just hit dapper-security. I presume this breaks FLAC playback again. Since I don't really want to upgrade to Edgy Eft just yet, has anyone got a patch ready to re-enable FLAC playback?

---

### Post by happyisland on 2006-12-05
I was wondering the same thing... Has anyone tried the new libxine and does it allow flac playback with Amarok? Also, what are the security consequences if I don't install the new libxine? I need my FLAC!

---

### Post by Rhapsody on 2006-12-05
I've just tried the latest libxine-main. It does indeed break FLAC playback in Amarok. Another patch will be required.

---

### Post by hvidgaard on 2006-12-06
If someone makes the patch and mail it to me @ [EMAIL="hvidgaard@daimi.au.dk"]hvidgaard@daimi.au.dk[/EMAIL] I will put it on my website asap :)

But until then, I suggest you downgrade to the lastest patched version ([http://hvidgaard.dk/download/xine-flac-update/](http://hvidgaard.dk/download/xine-flac-update/))

/Hvidgaard

---

### Post by steevc on 2006-12-07
I tried FLAC playback after the latest libxine update and it's the same as before, i.e. can't fast forward and end of track gets cut off.

---

### Post by RAdams on 2006-12-30
> **seamus7 said:**
> I am on Ubuntu Edgy and installed Amarok 1.4.4. After I enabled libxine-extracodecs my flac files played and my cue sheets displayed. :)

[https://launchpad.net/distros/ubuntu/+source/amarok/+bug/64075](https://launchpad.net/distros/ubuntu/+source/amarok/+bug/64075)

!confirm. Anyone on Kubuntu Edgy, update apt, get libxine-extracodecs and you should be set.

---

### Post by Rhapsody on 2006-12-30
Doesn't do people on Dapper much good though. I just keep putting Edgy off over and over. Maybe it's time to make the jump...

---

### Post by RAdams on 2006-12-30
> **Rhapsody said:**
> Doesn't do people on Dapper much good though. I just keep putting Edgy off over and over. Maybe it's time to make the jump...

I recommend it, actually. I haven't faced any stability problems at all, except for two rather weird annoyances:

1) I had a program called keytouch, which allowed me to map my multimedia keyboard. Apparently, running the update to 6.10 caused it to crash the system! But given the debugging symbols, I'd have to point to keytouch as being the source of that.

2) My loading screen looks odd. But this is a known problem with 6.10 amd64, and they're working on it. It doesn't affect performance,

Other than that, I'm quite happy.

---

### Post by Sweet Spot on 2007-01-02
Not quite sure I'm ready to make the jump to Edgy, since I'm really still getting very comfy with Dapper, and like the stability it has been offering me. I've got my routine w/it now, and fear for losing that edge. 

Is anyone perhaps working on the patch to re-enable FLAC playback ?

---

### Post by dorcssa on 2007-01-05
Well, that's wierd. I can play flac files, but I recently got hair in flac, and amarok just jumps over them, don't wanna play them. But I can play other flac files other than that album...

---

### Post by RSX311 on 2007-01-07
> **dorcssa said:**
> Well, that's wierd. I can play flac files, but I recently got hair in flac, and amarok just jumps over them, don't wanna play them. But I can play other flac files other than that album...

I have the same problem and can't figure it out.  It will play a few other flac albums though.

---

### Post by dorcssa on 2007-01-08
> **RSX311 said:**
> I have the same problem and can't figure it out.  It will play a few other flac albums though.

And the problem can't be with the files, coz vlc, or mplayer would play them out of the box. :-k

---

### Post by RSX311 on 2007-01-08
> **dorcssa said:**
> And the problem can't be with the files, coz vlc, or mplayer would play them out of the box. :-k

exactly, it'll play perfectly in Songbird and Rhythmbox but not Amarok :(

---

### Post by solderhead on 2007-01-14
> **RAdams said:**
> !confirm. Anyone on Kubuntu Edgy, update apt, get libxine-extracodecs and you should be set.

well, that didn't help.  i already had lixbine-extracodecs installed.  i still have the problem where amarok passes over .flac files that can be played by other apps like juk.

---

### Post by hanexar on 2007-01-17
Ok, I'm bringing it again:

I just install amarok a few days ago, and I just loved it, until I find out that my flac files won't play. 

I found the libxine patch, but I had already upgraded to the 1.1.1+ubuntu2-7.5 version. So I can't install the patch because it is an older version, I can't remove only the file without removing amarok. 

What should I do to get this working ?

---

### Post by dorcssa on 2007-01-18
You have to remove amarok in order to install that older version. I know, I tried it.Uninstall libxine, itt will remove amarok too, then install the patch deb, lock the version, and install amarok again. I see no other way, but it's not a big deal.

---

### Post by hanexar on 2007-01-18
thanx, it may have been said before, but could you tell me how to lock a version?

EDIT: Just made my homework: Package menu in synaptic then force version.

---

### Post by Sweet Spot on 2007-01-23
I'm going to do this ^^ but which of the patch links do I click on ? > 
  [Parent Directory]("http://hvidgaard.dk/download/")                                21-Jan-2007 14:11      -  
  [libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")   10-Oct-2006 17:51   113k  
  [libxine-dev_1.1.1+ubuntu2-7.3+patch1_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-dev_1.1.1+ubuntu2-7.3+patch1_i386.deb")   10-Oct-2006 17:51   113k  
  [libxine-dev_1.1.1+ubuntu2-7.3-patch0_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-dev_1.1.1+ubuntu2-7.3-patch0_i386.deb")   10-Oct-2006 17:51   113k  
  [libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb") 10-Oct-2006 17:52   3.0M  
  [libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-main1_1.1.1+ubuntu2-7.2_amd64.deb")       10-Oct-2006 18:46   2.6M  
  [libxine-main1_1.1.1+ubuntu2-7.3+patch1_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-main1_1.1.1+ubuntu2-7.3+patch1_i386.deb") 10-Oct-2006 17:53   3.0M  
  [libxine-main1_1.1.1+ubuntu2-7.3-patch0_i386.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-main1_1.1.1+ubuntu2-7.3-patch0_i386.deb") 10-Oct-2006 17:54   2.9M  
  [libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb]("http://hvidgaard.dk/download/xine-flac-update/libxine-main1_1.1.1+ubuntu2-7.3_amd64.deb")       10-Oct-2006 17

I know it's not the AMD 64 bit, cus I don't have that processor. But besides that, what's my indicator ?

---

### Post by Sweet Spot on 2007-01-23
Well, nevermind. Thanks to the above 2 posts, I've got FLAC working again. Why though, hasn't this been updated in the newest version of Amarok ?

---

### Post by RAdams on 2007-02-08
Because Feisty will feature [on-demand installation of codecs](http://www.flickr.com/photos/28313023@N00/375559390/in/set-72157594510537135/), so why bother patching Amarok when the new version is out in two months and 11 days? We're just along for the ride until then. :popcorn:

---

### Post by beastly on 2007-02-09
Can anyone explain how to perform this patch on an AMD64 Edgy system? I've tried the patches but Amarok still doesn't work properly. I can play FLAC files in it fine by loading them directly through the file browser (although it doesn't seem to be able to read the tags, instead just showing the filename) but none of them show up in the collection.

I've checked all my FLAC files are OK (using flac -t $file for all my collection) and also checked they don't have ID3 tags, only Vorbis tags. They all report back as FLAC files using the file command.

Thanks.

---

### Post by dorcssa on 2007-02-10
There was a patch specially for 64bit, as I remember..have you used that?

---

### Post by beastly on 2007-02-12
Yes I tried installing the patch, and various other tricks mentioned in this thread, but it doesn't seem to have worked. Can anyone explain why there are a total of 6 patches for i386 but only 2 for AMD64?

[http://www.hvidgaard.dk/download/xine-flac-update/](http://www.hvidgaard.dk/download/xine-flac-update/)

Cheers.

---

### Post by k2t0f12d on 2007-03-06
> **dorcssa said:**
> Well, that's wierd. I can play flac files, but I recently got hair in flac, and amarok just jumps over them, don't wanna play them. But I can play other flac files other than that album...

Same problem with FLAC files I created with EAC in Feisty.  Feisty's Amarok played them but Edgy's does not.

> **dorcssa said:**
> And the problem can't be with the files, coz vlc, or mplayer would play them out of the box. :-k

This isn't true at all.  The problem is *definitely* with the files.  The files that are jumped over are reported as:```
k2t0f12d@ZEUS:~/rox/audio/flac/Joe Satriani/Joe Satriani$ file 01\ Cool\ #9.flac
01 Cool #9.flac: MP3 file with ID3 version 2.3.0 tag
```

FLAC that is playable in Amarok on Edgy report:```
k2t0f12d@ZEUS:~/rox/audio/flac/Joe Satriani/(1992) The Extremist$ file 01\ -\ Friends.flac
01 - Friends.flac: FLAC audio bitstream data, 16 bit, stereo, 44.1 kHz, 9244536 samples
```

If you convert your unplayable FLAC to WAV and then reencode to FLAC, the reencodes will play, but this will delete all your metadata.  If you can use the FLAC to reassemble the original disc, you can CDDB it and reencode with new tags.  Otherwise, if anyone has any idea how to change the wrapper on the Mp3 doppleganger FLACs back to FLAC please post it so we can correct our files without a lot of redundant work.

---

### Post by Sweet Spot on 2007-06-11
This is really pissing me off to no end. Why won't the Amarok devs just fix the FLAC playback problem ? At this point, if I could find another suitable database type player like Amarok, I'd switch in a heart beat. 

Every other month or so, it seems that I have to try and re-apply some patch to make FLACs work, but now, I can't even do that. I have all the official repositories, as well as universe ones enabled, and update everything as often as possible. I guess I have the most recent versions of libxine main and dev which are available, and the code listed earlier in this thread to patch it up, just won't work anymore. says directory doesn't exist. (typical). 

And when I tried the other patches, I get dependency issues, and am also told that I have a later version of libxine main, and if I'm to uninstall that particular thing, it also wants to uninstall other stuff besides Amarok, which makes ZERO sense to me. Why can't you just uninstall a plugin without the rest of the components which rely on it ?  

So ok, what the heck should I do now ? Get a different player, or what ?  I'm running Dapper 6.06 still which IS LTS, and see no reason for me to jump to any other unstable, or test release at this point. Dapper has 'just worked' for me, so I ain't leaving it. (aside from this crap, which isn't Dappers fault)

Doug

---

### Post by Tzuny on 2007-12-01
Thank U, Thank U, Thank U very much for the debs!!!!!!!!!!
FLAC working very well right now!!!!!!!!!!!!!!!!!!!

---

### Post by raziv on 2008-01-20
Amarok broken again ](*,)
I had to downgrade to previous version: I had two options in synaptic's "force version" option under "package" menu - one from "dapper-update" the older from "dapper". After that I reinstalled ivoman's patch (quoted below) and regained flac capability :|. Any pro out there with the know-how to create a patch for the new version? How come it didn't get in the ubuntu repositories already anyway :??
> **ivomans said:**
> Right now I'm listening to a flac file on Amarok 1.4.1 :D 

I just merged  [this patch]("http://bugs.kde.org/attachment.cgi?id=16315&action=view") with the current Dapper version 1.1.1+ubuntu2-7.2. 

I'm not an experienced packagebuilder at all, but at least it works for me. You could try it by downloading at least my file at underneath link "1", then give the command:
```
sudo dpkg -i libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb
```
After this you'll need to restart Amarok.

Hope this helps others as well. But of course best would be an official patch in the (k)ubuntu repositories.

[LIST=1]
[*][libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-main1_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[*][libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb]("http://www.databrowser.org/download/libxine-dev_1.1.1+ubuntu2-7.2+patch1_i386.deb")
[/LIST]
raziv

---

