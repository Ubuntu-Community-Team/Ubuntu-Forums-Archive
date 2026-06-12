---
title: "How to install Samba GUI in Ubuntu 20.04"
date: 2020-04-29
forum: Desktop Environments
---

### Post by kamathlokesh on 2020-04-29
Hi All,

Yesterday I have installed Ubuntu20.04 and trying to install Samba GUI via terminal with below command

system-config-samba

this is not working. So can any help me for this?

Thanks in advance.

Lokesh Kamath.

---

### Post by Morbius1 on 2020-04-29
system-config-samba was removed from the repositories back in 19.04.

---

### Post by kamathlokesh on 2020-04-29
Thanks for your response.

How to install Samba GUI? What are the other options?

Lokesh Kamath

---

### Post by Morbius1 on 2020-04-29
edit /etc/samba/smb.conf directly.

---

### Post by kamathlokesh on 2020-04-29
Thank you.

So no GUI?

Lokesh Kamath

---

### Post by CelticWarrior on 2020-04-29
I think there's a sort of similar KDE package still around. Why don't you search for "samba" in the app store?

---

### Post by kamathlokesh on 2020-04-29
Wow.. 
Thank you so much.

I will try to install through app store.

Lokesh Kamath

---

### Post by Tadaen_Sylvermane on 2020-04-30
I don't mean to be harsh but in the time it may take you to find a working useful gui for something like that, you could google and configure the smb.conf file directly in about 2-3 minutes. 10 tops if it's remotely complex (usually isn't). Just saying.

---

### Post by zpangwin on 2020-07-04
This thread comes up in a lot of google searches for system-config-samba (which I will refer to as SCS here) in relation to Ubuntu 20.x/Ubuntu 19.x and Ubuntu-derivatives based on these versions (such as the recently released Linux Mint 20). I felt the answers in this thread were incomplete and would like to attempt to add to them from my own research.

**Why Was System Config Samba Even Removed?**

I am not close to this but my guess was that ultimately it was removed because a) it was using deprecated python2 libraries which were slated for removal, b) there was no maintainer and it hadn't been updated in ages, c) there were multiple existing issues which prevented it from even being launched after installation. For (c), I am  meaning specifically the [/etc/libuser.conf bug]("https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/1387274") and the gksu reference in its *.desktop file (as opposed to polkit).

Personally, I think (a) is the largest contributing reason since I've seen a couple other apps depending on old python2 libs that were removed as well. I know for sure that fslint was also removed and that both it and SCS depended on python-glade2, which was also removed.

**Options for Samba:**

1. Use an alternative Samba GUI such as "gadmin-samba". "[TechRepublic - 5 Tools for Configuring Samba]("https://www.techrepublic.com/blog/five-apps/five-tools-for-configuring-samba/")" mentions a few option."[Samba.org - Samba GUI page]("https://www.samba.org/samba/GUI/")" also contains some options but it lists samba apps for a variety of purposes, not only ones for configuring shares. There are also some file manager plugins that might work (e.g. "caja-share" for MATE, "nemo-share" for Cinnamon, "nautilus-share" for GNOME3, etc) but I haven't tried them so am not sure if these allow *configuring* or just *accessing* samba shares. For me personally, I still prefer SCS's UI layout but I am grateful that alternatives exist.

2. "Honey Badger Don't Care": technically, you can still get SCS to run by installing old deb packages for it and any deprecated libraries it depends on. However, you will still need to deal with other major issues I mentioned above and realize this is not supported and could break again due to future system changes. IMO manually installing from old deb files is NOT the hardest part about this approach; the polkit stuff takes the cake there. If you are interested in doing this, see [my notes on github]("https://github.com/zpangwin/linux-setup-scripts/tree/master/mint-20.x/apps/samba-config"); I have a bash script there that automates the process. I have only validated the script against Mint 20.0 thus far but I am not aware of anything in Ubuntu 20 that would require additional changes.

3. As has been pointed out by others in this thread and elsewhere on the web, Samba config primarily uses a single text file /etc/samba/smb.conf which can be edited directly and contains comment code that should help. If you get stuck there's "man smb.conf" and tons of examples online. I also include a samble smb.conf under the github folder linked to in the previous bullet. I can understand both sides here: this option is not a strictly valid answer to a question specifically asking for a GUI. Yet GUI's are intended to simplify and editing a text file is fairly simple. I have found in the past that even with SCS, I still had to edit the file directly from time to time and I *always* had to drop to terminal and use **sudo smbpasswd -a "smb_user_name"** because SCS never set up new users correctly for me.

4. Use something else instead of Samba: There are GUI options available for other protocols which work well on LANs such as SFTP via filezilla / NFS via [Simple NFS GUI]("https://www.linuxuprising.com/2018/11/easy-nfs-share-setup-in-ubuntu-linux.html")[ [github]("https://github.com/Philippe734/Simple.NFS.GUI")]. *Note: I have only used Filezilla for SFTP over SSH on Linux-to-Linux setups and have not used NFS at all (yet) myself. Plus YMMV depending on your setup / if you have to deal with setting up SSH or SFTP on a Windows box / etc.*

5. Roll your own. I know that generally people don't like a response like this when they are looking for a working solution. But that is why I included as the *last* of several options and I'd also point out that I am including it not to mock/condescend to anyone but rather to potentially inspire someone. If you don't like what's out there, by all means, please create something even better. And if you just wish you could have system-config-samba under python3, you could even extract its sources from one of the [system-config-samba DEB files]("https://packages.ubuntu.com/bionic/all/system-config-samba/download") using file-roller/etc and migrate the code (personally, I would guess building one from scratch to be less work but don't let me stop you!).

---

### Post by rsteinmetz70112 on 2020-07-05
Just be careful while configuring samba from web pages, while more are mostly right there have been a lot of changes to samba moving from samba3 to samba4 and there are a lot of existing pages that don't cover these options, especially if you're configuring an AD back end.

---

