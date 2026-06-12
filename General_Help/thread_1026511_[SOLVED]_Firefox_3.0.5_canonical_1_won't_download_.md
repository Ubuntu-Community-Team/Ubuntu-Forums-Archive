---
title: "[SOLVED] Firefox 3.0.5 canonical 1 won't download anything"
date: 2008-12-31
forum: General Help
---

### Post by quadrantids on 2008-12-31
Hello,

I'm using Intrepid under wubi on a DELL Inspiron 8200. So far I've been really happy with the experience but recently, the download function in Firefox has stopped working.

I have tried reconfiguring firefox (sudo dpkg-reconfigure firefox). I then tried reinstalling firefox using synaptic.

All that seems to be left is to reinstall wubi...

Can anyone please help? In the meantime I'm using Opera (which does download successfully).

Thx

---

### Post by dcstar on 2008-12-31
> **quadrantids said:**
> Hello,

I'm using Intrepid under wubi on a DELL Inspiron 8200. So far I've been really happy with the experience but recently, the download function in Firefox has stopped working.

I have tried reconfiguring firefox (sudo dpkg-reconfigure firefox). I then tried reinstalling firefox using synaptic.

All that seems to be left is to reinstall wubi...

Can anyone please help? In the meantime I'm using Opera (which does download successfully).

Thx

Close Firefox, rename the hidden .mozilla directory and then restart Firefox.

---

### Post by quadrantids on 2009-01-01
David,
Thx: but how do I do that?

Robert

---

### Post by zika on 2009-01-01
> **quadrantids said:**
> David,
Thx: but how do I do that?

Robert
I assume You know how to close Firefox ... :)

open Terminal (Applications->Accessories->Terminal) and type "gksudo nautilus" on prompt. give Your pass when asked. When nautilus opens go to "home". Click Ctrl-H and find directroy named ".mozilla". right-click then Rename and give it some name that You will remember. Ctrl-H and close nautiilus. do not do anything else in that nautilus window since it is administrative privileged window.

start firefox and enjoy.

---

### Post by bumanie on 2009-01-01
Personally I would remove firefox and reinstall it - I had to do that yesterday and it works great now. If you wish to know how, post again - it's quite easy.

---

### Post by zika on 2009-01-01
> **bumanie said:**
> Personally I would remove firefox and reinstall it - I had to do that yesterday and it works great now. If you wish to know how, post again - it's quite easy.
personally I would install shiretoko ... ;) actually I did ... ;) [http://ubuntuforums.org/showpost.php?p=6462096&postcount=41](http://ubuntuforums.org/showpost.php?p=6462096&postcount=41) 

so, do what dcstar told You, I've explained, try it and then unpack shiretoko ... ;)

---

### Post by quadrantids on 2009-01-01
> **zika said:**
> I assume You know how to close Firefox ... :)

open Terminal (Applications->Accessories->Terminal) and type "gksudo nautilus" on prompt. give Your pass when asked. When nautilus opens go to "home". Click Ctrl-H and find directroy named ".mozilla". right-click then Rename and give it some name that You will remember. Ctrl-H and close nautiilus. do not do anything else in that nautilus window since it is administrative privileged window.

start firefox and enjoy.

Thx: I tried this and although there were several files ".something" I really couldn't find ".mozilla"...

---

### Post by quadrantids on 2009-01-01
As I mentioned at the outset, I tried uninstalling firefox and reinstalling using Synaptic but perhaps I didn't select the right files, so if you could tell me how to do so correctly I'd be grateful.

Robert

---

### Post by zika on 2009-01-01
> **quadrantids said:**
> Thx: I tried this and although there were several files ".something" I really couldn't find ".mozilla"...
can You give us the result of ```
ls -lag ~/.mozilla
``` in Your terminal window. I hate suggesting to somebody to do something that looks like ```
mv ...
``` before I can be resonably sure what is the real situation on a machine I can't see.

---

### Post by zika on 2009-01-01
> **quadrantids said:**
> As I mentioned at the outset, I tried uninstalling firefox and reinstalling using Synaptic but perhaps I didn't select the right files, so if you could tell me how to do so correctly I'd be grateful.

Robert

let's try and make a Shiretoko (Firefox 3.1beta3 leading to 3.1RC and 3.1 finally, more restricted and less experimental now) work for You.

let's assume that You are using 64-bit version of Ubuntu. then the seqence of command would be (*position Yourself in Your home directory in Terminal window*):```
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/firefox-3.1b3pre.en-US.linux-x86_64.tar.bz2
sudo tar -xvf firefox-3.1b3pre.en-US.linux-x86_64.tar.bz2
cd firefox
sudo nano firefox
```if You are using 32-bit than You should use:
```
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/firefox-3.1b3pre.en-US.linux-i686.tar.bz2
sudo tar -xvf firefox-3.1b3pre.en-US.linux-x86_64.tar.bz2
cd firefox
sudo nano firefox
```either way in editor change the following:```
moz_libdir=/usr/local/lib/firefox-3.1b3pre
``` into ```
moz_libdir=/home/**Your_user_name**/firefox
``` or, even simpler, ```
moz_libdir=~/firefox
```put in System->Preferences->Prefered Applications->Web Browser->Custom->/home/**Your_user_name**/firefox and have it on Your favourite shortcut key ... and as a new default browser instead of (non)existing Firefox 3.0.5 or whatever.

this way you did not mess anything with Your operating system and once it is working OK You can think of reinstalling firefox that came with Ubuntu. removing directory ~/firefox removes (nearly) any effect my suggestion had on Your computer to the contrary to installing and reinstalling ... (to be clear, I'm using everything I have suggested on my every-day computer and several others on my LAN)

if You wish to use Minefield (a branch that is more experimental and will lead to version 3.2) than commands are:

```
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2
sudo tar -xvf firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2
cd firefox
sudo nano firefox
```if You are using 32-bit than You should use:
```
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/firefox-3.2a1pre.en-US.linux-i686.tar.bz2
sudo tar -xvf latest-mozilla-central/firefox-3.2a1pre.en-US.linux-i686.tar.bz2
cd firefox
sudo nano firefox
```[B]
Update: [/B]while reading some other threads I've stumbled upon a Firefox optimized version: Swiftweasel which I've just tried and got to love instantly because of the speed, the fact that it in sort inherits config from firefox but not share it, plugins are inherited, it brings some new ones, so things are even safer, withot need to create new profile, and it somehow feels great  (no, I'm not a new-stuff-junkey, quite contrary). 
installation is just the same as above:
```
wget http://downloads.sourceforge.net/swiftweasel/swiftweasel-3.0.5_amd-pgo_8.10-amd64.tar.gz?modtime=1230658069&big_mirror=0
sudo tar -xvf swiftweasel-3.0.5_amd-pgo_8.10-amd64.tar.gz
cd swifweasel
sudo nano firefox
```if You are using 32-bit than You should use:
```
wget http://downloads.sourceforge.net/swiftweasel/swiftweasel-3.0.5_amd-pgo_8.10-i386.tar.gz?modtime=1230658080&big_mirror=0
sudo tar -xvf swiftweasel-3.0.5_amd-pgo_8.10-i386.tar.gz
cd firefox
sudo nano firefox
```either way in editor change the following:```
moz_libdir=/usr/local/lib/firefox-3.0.5
``` into ```
moz_libdir=/home/**Your_user_name**/swiftweasel
``` or, even simpler, ```
moz_libdir=~/swiftweasel
```put in System->Preferences->Prefered Applications->Web Browser->Custom->/home/**Your_user_name**/swiftweasel

---

### Post by quadrantids on 2009-01-01
Thx for all the help: I ended up reinstalling wubi... Then I saw the above. I shall look at swiftweasel.

---

