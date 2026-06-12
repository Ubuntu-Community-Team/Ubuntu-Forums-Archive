---
title: "Firefox upgrade"
date: 2005-07-25
forum: Desktop Environments
---

### Post by Spleenie on 2005-07-25
Just got the security list email saying firefox upgrade is go.

Results of attempted installation of Firefox 1.06 and gnome support:

```
Preconfiguring packages ...
(Reading database ... 76395 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.4-1ubuntu3~5.04ubp5 (using .../mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.4-1ubuntu3~5.04ubp5 (using .../mozilla-firefox-gnome-support_1.0.6-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.6-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.6-0ubuntu0.1_i386.debE: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

Ooer...my pipe broke...ouch

help! :)

-  Spleenie

---

### Post by KLineD on 2005-07-25
Same here... unfortunately I tried a little "harder" to install it and now I don't have firefox in my machine... I'm posting this from another pc with windows...  [-X 

What to do?

---

### Post by claydoh on 2005-07-25
I got the same message and was successfull in installing 1.0.6 by first uninstalling the old firefox.

---

### Post by Rule on 2005-07-25
I just did the upgrade now on both ubuntu boxes and I got no errors :D

---

### Post by dtfinch on 2005-07-25
Today's update trashed everything having to do with firefox. I have no firefox as a result of the failed update, but synaptic says I have two.

Apt-get and synaptic refuse to remove "firefox" (which it already trashed) without upgrading "mozilla-firefox" first. Not sure why they're installed simultaneously in the first place. So I can't remove "firefox", can't update "mozilla-firefox", and if I want to remove "mozilla-firefox", it'll forcibly uninstall about 20 other packages. I'm simply locked out of having an ubuntu supported firefox package installed on my system. Maybe I'll try the nightlies.

---

### Post by SlugO on 2005-07-25
I got the same message. Then when I tried again I got this:

```
E: /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb:
trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which
is also in package firefox E: /var/cache/apt/archives/mozilla-firefox-gnome-
support_1.0.6-0ubuntu0.1_i386.deb:  trying to overwrite
`/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in
package firefox-gnome-support
``` 

Somebody please help :?

---

### Post by akshoslaa on 2005-07-25
[QUOTE=claydoh]I got the same message and was successfull in installing 1.0.6 by first uninstalling the old firefox.[/QUOTE]
 Fisrt I managed to break firefox completely... then came here... 1.06, now working ;)

$ sudo apt-get remove mozilla-firefox mozilla-firefox-gnome-support

(this will remove several other packages aswell, including ubuntu desktop)

$ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support plus whatever packages it-said it-was-removing

eg: $ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support mozilla-mplayer yelp ubuntu-desktop

it retained all me setting and (so far) all my extensions still work, so I'm happy.

Oh and those of us who applied the version hack to make 1.04 _look_ like 1.04 instead of .02 might want to change it back now :P (about:config -> filter "vendorSub"  -> "1.0.6")

my question is what caused this? I assume it was checked  and worked before it made release, so it's likely something we've done....

I know I had to apply the version hack to use the moz-extension page, and I'd changed all the default icons from the ubuntu ones to the firefox ones (as per ubuntuguide)

Apart from that, I can't think of anything...

other people who hit this... what do you think caused it?
(about to test it on my secondry system that had neither the version hack, nor the icons replaced... will let you know how it goes...)

---

### Post by Coogan on 2005-07-25
Count me in among those with broken Firefox packages.  Tried everything suggested in this thread and so far zilch.  Guess it's back to Lynx  ](*,)

---

### Post by dtfinch on 2005-07-25
This worked for me:

dpkg --force-depends -r firefox firefox-gnome-support
apt-get -f dist-upgrade

---

### Post by KLineD on 2005-07-25
I did what akshoslaa said and still got the same results. I managed to install firefox from getfirefox.com that I got from another machine, but still cant install the ubuntu package.

Actually, the package installs fine but when I try to launch it, the taskbar gets a Starting firefox window and then it just dissapears. If I try to launch it from the console using "firefox %u" or simply "firefox" it just ends silently with no error

---

### Post by SlugO on 2005-07-25
[QUOTE=akshoslaa]
$ sudo apt-get remove mozilla-firefox mozilla-firefox-gnome-support

(this will remove several other packages aswell, including ubuntu desktop)

$ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support plus whatever packages it-said it-was-removing
[/QUOTE]
Thanks akshoslaa, it worked for me too. I was getting really pissed off with this update. Thank god for Opera.
I'm really surprised that they released an update this buggy...

---

### Post by dtfinch on 2005-07-25
I got that too after resolving the update problem. For some reason, the entire time there was an instance of firefox-bin crashed in the background.

Everything worked once I killed the process.

---

### Post by akshoslaa on 2005-07-25
[QUOTE=Coogan]Count me in among those with broken Firefox packages.  Tried everything suggested in this thread and so far zilch.  Guess it's back to Lynx  ](*,)[/QUOTE]


that's one thing I noticed... 
$ apt-get remove firefox firefox-gnome-support
tried to install the mozilla-* packages aswell as removing the firefox ones... which didn't work...

I had to
$ apt-get remove **mozilla-**firefox **mozilla-**firefox-gnome-support

me thinks maybe there's been a change in package name... I know the firefox and mozilla-firefox packages are the same thing, but maybe it was installed initilly calling itself firefox, and doesn't like the name-change...

It didn't work smoothly on my secondry system (the one without random changes applied to it) either... but apt-get remove etc did the trick...
I'm about to test it on a completely clean system I've got installed (for testing) but I don't hold out much hope...

---

### Post by Coogan on 2005-07-25
[QUOTE=dtfinch]I got that too after resolving the update problem. For some reason, the entire time there was an instance of firefox-bin crashed in the background.

Everything worked once I killed the process.[/QUOTE]

Thanks for the tip.  I had an instance of firefox-bin running in the background as well.  Kill it, started Firefox.  It started just fine.  Was then able to run apt-get for the update and it installed and ran perfectly as well.

---

### Post by KLineD on 2005-07-25
That was it. It's all good now but I trashed the .mozilla directory so I lost all my bookmarks and extensions.

Nothing to worry about since I have a backup  :razz:

---

### Post by akshoslaa on 2005-07-25
[QUOTE=dtfinch]This worked for me:

dpkg --force-depends -r firefox firefox-gnome-support
apt-get -f dist-upgrade[/QUOTE]


I was just wondering if dist-upgrade would work... :P

---

### Post by vol_freak on 2005-07-25
[QUOTE=Coogan]Thanks for the tip.  I had an instance of firefox-bin running in the background as well.  Kill it, started Firefox.  It started just fine.  Was then able to run apt-get for the update and it installed and ran perfectly as well.[/QUOTE]

Same here. I FINALLY got it working now. I swore I looked to see if there was an instance of firefox already running in the background. Thanks to everyone who contributed! (I love the ubuntu forums  :) )

---

### Post by akshoslaa on 2005-07-25
As an interesting side note, just finished the apt-get upgrade on a clean system...

1.06 installed flawlessly...

this system however _didn't_ have 1.04 installed already (was still on the default 1.02 from the cd)

could it be that the 1.04 was more messed up than we thought? and there's actually nothing wrong with 1.06?

Curious to figure out how something like this managed to slip through...

---

### Post by NeoChaosX on 2005-07-25
The problem was if you had Ubuntu Backports repos in your apt sources. The latest versions of Firefox from Backports are labeled "firefox" (because that's how they're named in Breezy) and the mozilla-firefox packages installed with Hoary are replaced with dummy packages to help maintain compatiblity with Hoary. However, the update was for the main Hoary packages, not the backported firefox packages. Thus, the conflict since we have two different Firefox installs on the same system.

---

### Post by senectus on 2005-07-25
[QUOTE=dtfinch]This worked for me:

dpkg --force-depends -r firefox firefox-gnome-support
apt-get -f dist-upgrade[/QUOTE]

This did it for me too.. thanks very much

---

### Post by jeremy on 2005-07-26
There is a fixed update available in the repos now:
[http://ubuntuforums.org/showthread.php?t=51926](http://ubuntuforums.org/showthread.php?t=51926)

---

### Post by SlugO on 2005-07-26
Well I got Firefox working again after reinstalling it (and completely removing "firefox" package in the process). But now it's asking me to make a smart upgrade through Synaptic. It wants to update mozilla-firefox  and mozilla-firefox-gnome-support from 1.0.6-0ubuntu0.1 to 1.0.6-1ubuntu1~5.04ubp1. And also install firefox and firefox-gnome-support again.

Seriously. What the hell is going on in the repositories? Several versions of Firefox? And they're all messing each other up? Two 1.0.6 updates in two days? This situation seems **very** confusing. There is **no** way I'm updating Firefox again now that I got it working. I'm absolutely positive that this "smart" upgrade would break it again.

---

### Post by jocknerd on 2005-07-26
[QUOTE=akshoslaa]Fisrt I managed to break firefox completely... then came here... 1.06, now working ;)

$ sudo apt-get remove mozilla-firefox mozilla-firefox-gnome-support

(this will remove several other packages aswell, including ubuntu desktop)

$ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support plus whatever packages it-said it-was-removing

eg: $ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support mozilla-mplayer yelp ubuntu-desktop

it retained all me setting and (so far) all my extensions still work, so I'm happy.

Oh and those of us who applied the version hack to make 1.04 _look_ like 1.04 instead of .02 might want to change it back now :P (about:config -> filter "vendorSub"  -> "1.0.6")

my question is what caused this? I assume it was checked  and worked before it made release, so it's likely something we've done....

I know I had to apply the version hack to use the moz-extension page, and I'd changed all the default icons from the ubuntu ones to the firefox ones (as per ubuntuguide)

Apart from that, I can't think of anything...

other people who hit this... what do you think caused it?
(about to test it on my secondry system that had neither the version hack, nor the icons replaced... will let you know how it goes...)[/QUOTE]

Thanks.  This helped me.  It looks like the package Firefox was the culprit.  After removing what you said to remove, I tried reinstalling the package firefox and it said that the package didn't exist any longer.  But mozilla-firefox installed fine after removing it.

---

### Post by joplass on 2005-07-26
[QUOTE=dtfinch]This worked for me:

dpkg --force-depends -r firefox firefox-gnome-support
apt-get -f dist-upgrade[/QUOTE]

Thanks for the post mate!
This is the only process that worked for me.

---

### Post by Spleenie on 2005-07-26
[QUOTE=joplass]Thanks for the post mate!
This is the only process that worked for me.[/QUOTE]

Agreed.

I note that firefox is back in the "being held back" part of the apt-get upgrade thingy again. 

I am running 1.06 now according to the "about" details.

So can I take from this thread that there are actually a few firefox versions floating around the repos?

---

### Post by thebrade on 2005-07-26
ridiculous... why change the name for breezy, thus leading to all these probs?

---

### Post by angkor on 2005-07-26
[QUOTE=SlugO]Seriously. What the hell is going on in the repositories? Several versions of Firefox? And they're all messing each other up? Two 1.0.6 updates in two days? This situation seems **very** confusing. There is **no** way I'm updating Firefox again now that I got it working. I'm absolutely positive that this "smart" upgrade would break it again.[/QUOTE]

[QUOTE=NeoChaosX]The problem was if you had Ubuntu Backports repos in your apt sources. The latest versions of Firefox from Backports are labeled "firefox" (because that's how they're named in Breezy) and the mozilla-firefox packages installed with Hoary are replaced with dummy packages to help maintain compatiblity with Hoary. However, the update was for the main Hoary packages, not the backported firefox packages. Thus, the conflict since we have two different Firefox installs on the same system.[/QUOTE]

and now they've fixed the name in backports so naturally you would get another update if you have backports enabled. I've got the backports commented out in my sources.list so the 1.06 update installed without a hitch.

---

### Post by LazyIvan on 2005-07-27
I too am having problems with the recent firefox upgrade.  I have tried this suggestion that dtfinch has given:

[QUOTE=dtfinch]This worked for me:

dpkg --force-depends -r firefox firefox-gnome-support
apt-get -f dist-upgrade[/QUOTE]

But with one problem:
  when running the dist-upgrade, it seems to be starting off fine, and then partway through it begins to output garbage characters, with english and chinese characters scattered throughout.  And it repeats these lines many times:
 "[Garbage characters]: binary operator expected"

and also:

   "/usr/sbin/update-mozilla-firefox-chrome: line 78: [: too many arguments"

and then after a few seconds the console will hang after some garbage characters.
Now, when I try to run 'sudo apt-get -f dist-upgrade' now it tells me an error message to manually run dpkg --configure -a 
When I do so, it does the same error as described above, as I believe it is trying to finish the dpkg that it was not able to finish.  Does anyone have any ideas on how to fix this?  This is my first run-through with ubuntu and linux, so something tells me that the answer will be blindingly obvious!

Thanks for any input


EDIT:  after examining it some more this morning, it looks like the problem occurs when trying to remove 'firefox'

EDIT2:  fixed the problem, it seems it is not a good idea to apt-get any source files when mucking around in the directory structure where firefox was located, upon deleting the files it downloaded, the update was able to complete.

---

### Post by manicka on 2005-07-27
I've always made it a standard policy to unsinstall and then reinstall any new version of Firefox on any distro I've used. 
This used to be the standard advice in the pre version 1.0 days and it's a habit I've kept up and has kept me hassle free when upgrades occur.

---

### Post by jcohen on 2005-07-27
Ubuntu has changed it's policy for Firefox security updates. From now on, the newest stable release of Firefox will be packaged in hoary-security if the new release contains a security update. For example, if Firefox 1.0.7 comes out tomorrow, it will be packaged in hoary-security and will be available to all hoary users. The current issue is that there are 2 available firefox 1.0.6 packages (one from hoary-secuirty and one from Backports. Many users also had problems upgrading from backport's 1.0.4 to hoary-security 1.0.6 because of a packaging error.

Backports will also continue packaging new upstream releases of Firefox, whether or not a security issue is fixed. I suggest that users switch to the Official Backports repository which fixes this problem. 
[http://www.ubuntuforums.org/showthread.php?p=273253#post273253](http://www.ubuntuforums.org/showthread.php?p=273253#post273253)
The official backports repository (which uses the Ubuntu mirrors and has signed packages) uses a new naming convention and Firefox packages in hoary-security will be chosen over Backports if the versions are equal.

To fix the situation:

1) sudo gedit /etc/apt/sources.list. Uncomment or delete your hoary-backports line and replace it with "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted"

1) sudo apt-get update

2) sudo apt-get remove mozilla-firefox firefox

3) sudo apt-get install mozilla-firefox ubuntu-desktop 

You'll want the ubuntu-desktop package which was removed by uninstalling mozilla-firefox when you upgrade to breezy in a few months.

---

### Post by jcohen on 2005-07-27
I recommend that users stick with the hoary-security version of Firefox. Now that Ubuntu has decided to package the latest upstream release, we should see much faster security updates for both Warty & Hoary. There's no real reason to use backport's Firefox at the moment, and there won't be until Firefox 1.5 comes out in September.

---

### Post by Luggy on 2005-07-28
I got myself a strange problem most likely caused by my stupidity.

I installed firefox 1.0.6 from the update and it worked (as in not crashing and tabs work) but I can't install newer extensions. I try and install adblock and I get this message:
> Adblock 0.5.2.039 could not be installed because it is not compatible with this version of Firefox. (Adblock 0.5.2.039 will only work with Firefox versions from 0.7+ to 0.10+)

I have my general.useragent.vendorSub set to 1.0.4 (as pre 1.0.5 / 1.0.6 build) does this value need to change now that it has been updated?

---

### Post by Toddy on 2005-07-28
I went back and reset mine to default, which restored it to 1.0.6 now...

---

### Post by Shaggy on 2005-07-28
I was just wondering, what's the drawback of not reinstalling ubuntu-desktop.  I fixed the problem on my own when I updated yesterday but didn't reinstall ubuntu-desktop. 
 
Is there any real harm in leaving it removed? Because if I remember correctly the package was only needed for new package installs, and dist upgrades.

---

### Post by Luggy on 2005-07-28
Here is a work around for getting adblock to work on 1.0.6. It might work if anyone is having trouble installing other firefox updates.

> 
Adblock install workaround

by Keith, July 28, 2005 5:14pm

I modified Ben's instructions to be a little easier to read and understand: 1. In the URL (address) box type: about:config 2. Change 'app.extensions.version' from "1.0" to ".10" 3. Change 'extensions.disabledObsolete' to "false" 4. Install adblock. It should not complain about the version again. 5. Change 'app.extensions.version' back to "1.0" 6. Restart firefox and adblock should be running.

---

### Post by manicka on 2005-07-28
[QUOTE=Shaggy]I was just wondering, what's the drawback of not reinstalling ubuntu-desktop.  I fixed the problem on my own when I updated yesterday but didn't reinstall ubuntu-desktop. 
 
Is there any real harm in leaving it removed? Because if I remember correctly the package was only needed for new package installs, and dist upgrades.[/QUOTE]
 no harm at all, you only have to reinstall it just before upgrading to breezy

---

