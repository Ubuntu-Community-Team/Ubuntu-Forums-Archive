---
title: "Compiz-Fusion dependencies prevent install"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by j_trune on 2007-10-05
Hello all,
So I'm running Ubuntu Dapper Drake and I'm trying to install Compiz-Fusion.  I've been following the guide to installing it on [_this_]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") website.  That guide was recommended to me by a member of this forum (though I'm not sure if it matters that the guide mentions that it's for feisty).  

Anyways I installed Envy and everything seems to work fine.  Then I went through the steps of the guide, but I hit a hitch on steps 3 and 4.  When I go through step 3 (the second command ("gpg --export --armor 81836EBF | sudo apt-key add -") tells me that ultimately no trusted keys were found, and when I type the second command it tells you to in step four I get a bunch of seemingly unresolved dependences and well, it doesn't work.  I know it doesn't work because the third command in step 4 tells me so as well as the fact that the terminal code says stuff wasn't installed.  Below is the terminal code from that I was talking about (where stuff goes wrong)....

[HTML]root@Emmeline:~# sudo aptitude install compiz compiz-gnome \
>
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins
  libcompizconfig0 libdecoration0 python-compizconfig
The following NEW packages will be automatically installed:
  compizconfig-settings-manager
The following packages have been kept back:
  libmagick9 libpq4 libsndfile1 libssl0.9.8 linux-headers-2.6.15-29
  linux-headers-2.6.15-29-386 linux-image-2.6.15-29-386 openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer openssl python-apt python-uno python2.4-apt
  ttf-opensymbol
The following NEW packages will be installed:
  compiz compizconfig-settings-manager
0 packages upgraded, 9 newly installed, 0 to remove and 26 not upgraded.
Need to get 4680kB of archives. After unpacking 16.7MB will be used.
The following packages have unmet dependencies:
  libcompizconfig0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  libdecoration0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
  compiz-plugins: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                  Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.                  Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                  Depends: libfuse2 (>= 2.6) but it is not installable
                  Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                  Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                  Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.2 is installed.
                  Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  python-compizconfig: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                       Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                       Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                       Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                       Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                       Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                       Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
                       Depends: python (>= 2.5) but 2.4.2-0ubuntu3 is installed.                       Depends: python-support (>= 0.3.4) but it is not installable
  compiz-core: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
               Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.  compiz-fusion-plugins-main: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                              Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                              Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                              Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                              Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                              Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                              Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                              Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                              Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-gnome: Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is installed.
                Depends: libbonobo2-0 (>= 2.15.0) but 2.14.0-0ubuntu2 is installed.
                Depends: libbonoboui2-0 (>= 2.15.1) but 2.14.0-0ubuntu1 is installed.
                Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                Depends: libdbus-glib-1-2 (>= 0.73) but 0.60-6ubuntu8.1 is installed.
                Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is installed.
                Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                Depends: libgnome-keyring0 (>= 0.7.1) but 0.4.9-1ubuntu1 is installed.
                Depends: libgnome-window-settings1 which is a virtual package.
                Depends: libgnomeui-0 (>= 2.17.1) but 2.14.1-0ubuntu3 is installed.
                Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is installed.
                Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                Depends: libpopt0 (>= 1.10) but 1.7-5 is installed.
                Depends: libwnck18 (>= 2.15.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
compiz [0.0.2-4ubuntu2 (dapper)]
compiz-gnome [0.0.2-4ubuntu2 (dapper)]
libxcomposite1 [1:0.2.2.2-0ubuntu2 (dapper)]

Keep the following packages at their current version:
compiz-core [Not Installed]
compiz-fusion-plugins-main [Not Installed]
compiz-plugins [Not Installed]
compizconfig-settings-manager [Not Installed]
libcompizconfig0 [Not Installed]
libdecoration0 [Not Installed]
python-compizconfig [Not Installed]

Leave the following dependencies unresolved:
compiz recommends compiz-kde
Score is -276

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  libmagick9 libpq4 libsndfile1 libssl0.9.8 linux-headers-2.6.15-29
  linux-headers-2.6.15-29-386 linux-image-2.6.15-29-386 openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer openssl python-apt python-uno python2.4-apt
  ttf-opensymbol
0 packages upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
[/HTML]

I feel like I've gotta be pretty close to getting this to work, but I just can't figure it out.  Any help would be greatly appreciated.

Thanks in advance.

---

### Post by Pumalite on 2007-10-05
When it told you no trusted keys were found, did you say 'yes' anyway?

---

### Post by LowSky on 2007-10-05
it looks like compiz need the newer versions of a few programs
```

libcompizconfig0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  libdecoration0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
  compiz-plugins: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                  Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.                  Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                  Depends: libfuse2 (>= 2.6) but it is not installable
                  Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                  Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                  Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.2 is installed.
                  Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  python-compizconfig: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                       Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                       Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                       Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                       Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                       Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                       Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
                       Depends: python (>= 2.5) but 2.4.2-0ubuntu3 is installed.                       Depends: python-support (>= 0.3.4) but it is not installable
  compiz-core: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
               Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.  compiz-fusion-plugins-main: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                              Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                              Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                              Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                              Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                              Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                              Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                              Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                              Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-gnome: Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is installed.
                Depends: libbonobo2-0 (>= 2.15.0) but 2.14.0-0ubuntu2 is installed.
                Depends: libbonoboui2-0 (>= 2.15.1) but 2.14.0-0ubuntu1 is installed.
                Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                Depends: libdbus-glib-1-2 (>= 0.73) but 0.60-6ubuntu8.1 is installed.
                Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is installed.
                Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                Depends: libgnome-keyring0 (>= 0.7.1) but 0.4.9-1ubuntu1 is installed.
                Depends: libgnome-window-settings1 which is a virtual package.
                Depends: libgnomeui-0 (>= 2.17.1) but 2.14.1-0ubuntu3 is installed.
                Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is installed.
                Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                Depends: libpopt0 (>= 1.10) but 1.7-5 is installed.
                Depends: libwnck18 (>= 2.15.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
```

---

### Post by j_trune on 2007-10-05
> **Pumalite said:**
> When it told you no trusted keys were found, did you say 'yes' anyway?

it didn't prompt me to respond.  It just went back to the "root@Emmeline:~#"

Here is the actual of what happens with step 3....

[HTML]root@Emmeline:~# gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: key 81836EBF: "Treviño (3v1n0) <trevi55@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@Emmeline:~# gpg --export --armor 81836EBF | sudo apt-key add -
OK
root@Emmeline:~# s
[/HTML]

---

### Post by Pumalite on 2007-10-05
It looks like it loaded the key. Do:
sudo apt-get update and see if you can continue with the process.

---

### Post by j_trune on 2007-10-05
The same thing happened.  It was as if nothing had changed.

---

### Post by Forlong on 2007-10-06
> **j_trune said:**
> So I'm running Ubuntu Dapper Drake and I'm trying to install Compiz-Fusion.  I've been following the guide to installing it on [_this_]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") website. 
That's the problem right there. You can't use Feisty-packages for Dapper.

---

### Post by j_trune on 2007-10-06
> **Forlong said:**
> That's the problem right there. You can't use Feisty-packages for Dapper.

Can you tell me how to fix this??

---

### Post by j_trune on 2007-10-06
I found [these]("http://ubuntu-tutorials.com/2006/06/18/xgl-compiz-nvidia-ubuntu-6061-dapper-drake/")  instructions.  Can you  tell me if they would work??

---

### Post by Forlong on 2007-10-06
First you have to decide what it is you want.

Do you want to stick with Dapper? Is there any good reason for you to do so?

If not, I'd recommend switching to a newer version of Ubuntu.
You could upgrade your system but then you would have to upgrade to Edgy, then to Feisty and in two weeks to Gutsy (if you want the latest applications available).


Personally, I'd recommend waiting for the Gutsy release and make a fresh install then. Compiz Fusion is installed by default there.

---

### Post by j_trune on 2007-10-06
Hmm...  Ok, that sounds good. 

Thanks

---

