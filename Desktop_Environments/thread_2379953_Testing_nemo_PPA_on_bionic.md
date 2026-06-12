---
title: "Testing nemo PPA on bionic:"
date: 2017-12-11
forum: Desktop Environments
---

### Post by ventrical on 2017-12-11
@mac4man

I went to this site: [https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)  and installed the ppa  for nemo3  for unity-session/unity-ppa and got :

```

E: The repository 'http://ppa.launchpad.net/webupd8team/nemo3/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Could you guide me where I went wrong or is it because it is bionic? (I seen they only upgraded to artuful).

regards..

---

### Post by Chanath on 2017-12-11
> **ventrical said:**
> @mac4man

I went to this site: [https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)  and installed the ppa  for nemo3  for unity-session/unity-ppa and got :

```

E: The repository 'http://ppa.launchpad.net/webupd8team/nemo3/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Could you guide me where I went wrong or is it because it is bionic? (I seen they only upgraded to artuful).

regards..

Go to /etc/apt/sources.list.d, open the webupd8 list and change the deb to artful. There is no ppa for bionic (yet). Then update again.  
That is,
first [COLOR=#333333]sudo add-apt-repository ppa:webupd8team/nemo3, 
then, go to /etc/apt/sources.list.d and open that webupd file. You'd see bionic there, inside the webupd8.list. Change it to artful. Save it. Then, do sudo apt update, and install nemo[/COLOR]

---

### Post by mc4man on 2017-12-11
See you have a thread..
I'd  suggest trying the nemo3 ppa with the artful packages, if they work you'd see basically what it brings to the table.

After  installing nemo you need to disable nautilus handling the desktop 
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
Set as default file manager with this - 
```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```
Then reboot.
The ppa has set nemo-desktop to run on a 2 sec delay after logging in, may not be needed.

---

### Post by mc4man on 2017-12-11
Otherwise I'll make  nemo slightly modified available via a ppa.
The changes are;
Removed #12_unity_launcher_support.patch which causes xdg folder quicklist items to show on & off like nautilus does when nemo handles the desktop
Replaced the .desktop with one that has xdg folder quicklists built-in.

---

### Post by ventrical on 2017-12-12
@mac4man

 I have a completely new problem. The team leader changed the 'Label'  and now it will not update the ppa for unity7. I had notified team leader.

Do you have a way I can workaround this without having to build a new ISO just yet?

```

E: Repository 'http://ppa.launchpad.net/unity7maintainers/unity7-desktop/ubuntu bionic InRelease' changed its 'Label' value from 'Unity 7 Testing' to 'Ubuntu-Unity-18.04-Testing'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```

Secondly .. your method worked with nemo ppa but I can't verifiy because I had installed  nemo method from the main  before I had changed  to name to artful in (other) so I am  working on fresh install. I have two other hard installs but I want to use this current machine from factor.

regards..

> **mc4man said:**
> Otherwise I'll make  nemo slightly modified available via a ppa.
The changes are;
Removed #12_unity_launcher_support.patch which causes xdg folder quicklist items to show on & off like nautilus does when nemo handles the desktop
Replaced the .desktop with one that has xdg folder quicklists built-in.

[s]Nautilus will not go away. I tried it on a completely different install with unity-session. All went well but there is no nemo to be found. Probably something I did not do.[/s]

Typed nemo in terminal and voila'.

> **mc4man said:**
> Otherwise I'll make  nemo slightly modified available via a ppa.
The changes are;
Removed #12_unity_launcher_support.patch which causes xdg folder quicklist items to show on & off like nautilus does when nemo handles the desktop
Replaced the .desktop with one that has xdg folder quicklists built-in.

Yes.. please  do .. I think we are on to something here.

There are some bugs (screenshot macro will not work etc.) but no show stoppers.

Thanks ..

regards..

Did this again:

After  installing nemo you need to disable nautilus handling the desktop 
     

     ```
gsettings set org.gnome.desktop.background show-desktop-icons false

```

Set as default file manager with this - 
     
```


     xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search


```


Then reboot.

And now the header menus on on the main header bar.

But nautilus will still not go.

---

### Post by zika on 2017-12-12
> **ventrical said:**
> Then reboot.Why reboot on *nix?

---

### Post by ventrical on 2017-12-12
> **zika said:**
> Why reboot on *nix?

I was just doing what mac4man recommended.

---

### Post by zika on 2017-12-12
> **ventrical said:**
> I was just doing what mac4man recommended.All the best...

---

### Post by mc4man on 2017-12-12
> **zika said:**
> Why reboot on *nix?
So users may still be using gdm3 & more often than not gdm3 needs a reboot

---

### Post by mc4man on 2017-12-12
> **ventrical said:**
> Yes.. please  do .. I think we are on to something here.

There are some bugs (screenshot macro will not work etc.) but no show stoppers.

Thanks ..

regards..
see here, read page 1st.
[https://launchpad.net/~mc3man/+archive/ubuntu/nemo-demo](https://launchpad.net/~mc3man/+archive/ubuntu/nemo-demo)

What's broken in general (not nemo specific) is alt+print no longer works in a unity session. This goes back to 17.10, no solution I found other than to rebind
(-using alt+Insert here, but this needs to be fixed.

---

### Post by ventrical on 2017-12-12
@mac4man,

Thanks so much. Would appreciate if you would leave it up a bit until I can test and build an ISO with it . Thanks. I'll report back in.

Regards..

---

### Post by thehannibal on 2017-12-12
I'd like to add that upgrading from Nemo 3.4 -> Nemo 3.6 required  me to add latest versions of `xapps-common` and `libxapp1`, a note on how  to do that is :

```

sudo add-apt-repository ppa:nilarimogard/test3
sudo apt update
sudo apt install xapps-common libxapp1

```

---

### Post by ventrical on 2017-12-12
@mac4man,hannibal,

I had a seamless install. Screenshot one key is working. Did not have to install any extras.

@mac4man.

1. Is there a way in terminal where I can set nemo to autostart after reboot?
2. Is there terminal command to pin it to the unity panel?

 I would like to build an ISO  with nemo as default. FM as a reference point.

Regards..

---

### Post by zika on 2017-12-13
> **mc4man said:**
> So users may still be using gdm3 & more often than not gdm3 needs a rebootI admit it is easier. But in testing it does not make sense to me. Getting to know what is needed to be restarted gives more insight than lot of other stuff. Simple reboot just masks all that in oblivion. Just my .02$... Even modern other OS's are nicely made/evolved to be rebooted only once in a while, when really needed...

---

### Post by ventrical on 2017-12-13
> **zika said:**
> I admit it is easier. But in testing it does not make sense to me. Getting to know what is needed to be restarted gives more insight than lot of other stuff. Simple reboot just masks all that in oblivion. Just my .02$... Even modern other OS's are nicely made/evolved to be rebooted only once in a while, when really needed...

It makes sense to me because if you run nemo in terminal after you load the ppa/ you will notice header bar indicators on the app(pulldown menus). When you reboot the indicators are up on the top unity indicator panel so it makes a big difference in my view. Also..I am using the ppa to build an iso for unity... so I will have to see how that all works out. but I aprpeciate your 2 cents always ;)

---

### Post by Chanath on 2017-12-13
@ mc4man

Thanks!
Got it installed. These packages > gist rake ruby ruby-did-you-mean ruby-json ruby-minitest ruby-net-telnet ruby-power-assert ruby-test-unit ruby2.3 rubygems-integrationalso got installed with it. Are they needed?

---

### Post by mc4man on 2017-12-13
> **Chanath said:**
> @ mc4man

Thanks!
Got it installed. These packages also got installed with it. Are they needed?
Those appear to come from libxapps-common & the newer version of nemo needs libxapps so yeah, needed.

---

### Post by mc4man on 2017-12-13
The reason for a new .desktop was to provide the expected quicklist entries all the time. 
What would be better would be to solve why those entries show up only when nemo (or nautilus in the current 18.04 with unity) has at least 1 window open, however no solution has ever been presented. A clue may be from the removed patch which still is in the ppa source, i.e. #12_unity_launcher_support.patch 

Please note that many of the added desktop actions in the .desktop I created are not translated so that is also an issue (not for me personally

An alternate would be to use the orig. or close to orig. .desktop & not have nemo handle the desktop, let nautilus do so. 
 I used that for some time & didn't really mind.. The only thing there is that the  r. click on Desktop context menu is nautilus, I think nemo's is better.
(- the orig. .desktop had an entry to open computer:/// I changed that to / as computer:/// is useless to me..

Small note about nemo's context menu on files, if you click on the little + icon at top of menu you get the full context menu, very handy..

---

### Post by ventrical on 2017-12-13
@mac4man

I tried to remove nautilus and it wants to remove ubuntu-unity-desktop also (which is the new label from the unity ppa.) I just wanted to test nemo with out nautilis so is there a workaround  for this so to not get ubuntu-unity-desktop pulled with nautilus?

Thanks..

---

### Post by ventrical on 2017-12-13
> **mc4man said:**
> 

Small note about nemo's context menu on files, if you click on the little + icon at top of menu you get the full context menu, very handy..

"Show more actions"  yes .. that is very nifty.

---

### Post by mc4man on 2017-12-14
> **ventrical said:**
> @mac4man

I tried to remove nautilus and it wants to remove ubuntu-unity-desktop also (which is the new label from the unity ppa.) I just wanted to test nemo with out nautilis so is there a workaround  for this so to not get ubuntu-unity-desktop pulled with nautilus?

Thanks..
What is address of that ppa?

---

### Post by ventrical on 2017-12-14
> **mc4man said:**
> What is address of that ppa?

[https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)

---

### Post by mc4man on 2017-12-14
> **ventrical said:**
> @mac4man

I tried to remove nautilus and it wants to remove ubuntu-unity-desktop also (which is the new label from the unity ppa.) I just wanted to test nemo with out nautilis so is there a workaround  for this so to not get ubuntu-unity-desktop pulled with nautilus?

Thanks..
Probably not as nautilus is marked as a dependency. If it was a recommend then it could be removed.
libnautilus-extension1a & nautilus-data are required, nautilus is not.

Likely at the end of the day nautilus should remain as default, nemo a user side option..

For yourself just go ahead & remove nautilus if you want to see, ubuntu-unity-desktop is just a meta package, does nothing but install it's depends & recommends

---

### Post by zika on 2017-12-14
Dependencies can be muted or overridden...

---

### Post by ventrical on 2017-12-14
> **mc4man said:**
> Probably not as nautilus is marked as a dependency. If it was a recommend then it could be removed.
libnautilus-extension1a & nautilus-data are required, nautilus is not.

Likely at the end of the day nautilus should remain as default, nemo a user side option..

For yourself just go ahead & remove nautilus if you want to see, ubuntu-unity-desktop is just a meta package, does nothing but install it's depends & recommends

@mac4man

Thanks. That was the right stuff. I also updated the other ppa files:

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  a11y-profile-manager-indicator adduser apport apport-gtk binutils
  binutils-common binutils-x86-64-linux-gnu caribou compiz compiz-core
  compiz-gnome compiz-plugins-default evince evince-common gir1.2-caribou-1.0
  gir1.2-gtksource-3.0 gstreamer1.0-clutter-3.0 indicator-keyboard
  liba11y-profile-manager-0.1-0 liba11y-profile-manager-data libbinutils
  libcaribou-common libcaribou0 libclutter-gst-3.0-0 libclutter-gtk-1.0-0
  libcolord-gtk1 libcompizconfig0 libdecoration0 libevdocument3-4 libevview3-3
  libfftw3-double3 libfftw3-single3 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libunity-control-center1 lsb-base lsb-release
  python3-apport python3-problem-report unity-accessibility-profiles
  unity-control-center
41 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,795 kB/9,283 kB of archives.
After this operation, 524 kB disk space will be freed.
Do you want to continue? [Y/n] y

```

logoff/logon

and works just swell. So I will build an ISO for those who just want to test nemo with unity7.  They can run nemo and pin it to the unity panel. it looks set that nautilus will be default FM for (18.04) and I don't have a problem  with it either way.  nemo just offers a more classical user assistance motif which a lot of end_users like. so if it ain't broke ., dont fix it ;)

---

### Post by ventrical on 2017-12-14
@mac4man,

jbicha mentioned on the hub;

> 
Please add it to your todo list to forward your Nemo changes to the Debian Nemo maintainers.

[https://community.ubuntu.com/t/unity7-desktop-development-roadmap/2693/17?u=dale-f-beaudoin](https://community.ubuntu.com/t/unity7-desktop-development-roadmap/2693/17?u=dale-f-beaudoin)


regards

---

### Post by mc4man on 2017-12-14
> **ventrical said:**
> @mac4man,

jbicha mentioned on the hub;


[https://community.ubuntu.com/t/unity7-desktop-development-roadmap/2693/17?u=dale-f-beaudoin](https://community.ubuntu.com/t/unity7-desktop-development-roadmap/2693/17?u=dale-f-beaudoin)


regards
There is nothing to forward. Note that all the patches are from the nemo3 ppa, designed for nemo's use in unity.
Really who you should contact is the WebUpd8” team to see if they intend to do a version for bionic.

All I changed was to not apply 2 patches & patch the nemo.desktop.in.in file to suit my preferences. That .desktop patch is not acceptable as it's not fully translated, more to show what could be done if the sometimes show sometimes not show on desktop actions is either an issue or if an issue not solvable..

---

### Post by ventrical on 2017-12-14
> **mc4man said:**
> There is nothing to forward. Note that all the patches are from the nemo3 ppa, designed for nemo's use in unity.
Really who you should contact is the WebUpd8” team to see if they intend to do a version for bionic.
.

^^^

..and did the above.

Thanks..

---

### Post by khurshid.alam on 2017-12-18
I like the progress being made here. @mc4man suggested to keep the desktop handling of nautilus intact. But Nautilus is going to remove desktop handling altogether this cycle. I don't know whether Ubuntu maintain it as separate binary, but we should be ready if they doesn't. Nautilus has gnome-user-share. (Try running **/usr/bin/gnome-file-share-properties** from terminal). Does Nemo has something similar? I know it has nemo-share which equivalent of nautilus-share. 

If not, for greater integration with Unity I would prefer caja+mate-user-share. If Ubuntu/Gnome dropped desktop handling from nautilus we have two good options for replacement Caja and Nemo. We need to check more integration for both.

Edit: About quicklist, for Nemo, I can create a patch for dynamic quicklist.

---

### Post by QIII on 2017-12-18
Is this thread a discussion about a development version of an official Ubuntu flavor?

I don't believe Unity is included as an official flavor of Bionic.

---

### Post by mc4man on 2017-12-18
> **QIII said:**
> Is this thread a discussion about a development version of an official Ubuntu flavor?

I don't believe Unity is included as an official flavor of Bionic.
It's not a "flavor", it's a package that is in the 18.04 Ubuntu repos

---

### Post by QIII on 2017-12-18
It is available in the Universe repository.  It is something available.  No doubt.  But what is going on here is not a discussion about a package that is available, but Ubuntu with Unity as a development version.

It's not.

Again, if you want to talk Unity you are free to do so.  But not in this area of the forum and not as a development team discussion room.

---

### Post by ventrical on 2018-01-04
> **mc4man said:**
> It's not a "flavor", it's a package that is in the 18.04 Ubuntu repos

@mac4man,

Thanks for your help in this matter.


@QIII

The images have been moved from the archive. The thread is no longer needed. You can close.


Regards..

---

### Post by slickymaster on 2018-01-04
Closed per OP request

---

### Post by slickymaster on 2018-01-05
Thread reopened and moved to **Desktop Environments**

---

### Post by ventrical on 2018-01-05
@mac4man,

 I moved the nemo based iso to  the folder/nemo-iso.  

Will the ppa be active up and to the end of the 18.04 cycle? It is such a good fit for that shell. I would like to do another build of it after Jan.9th.

Regards..

---

