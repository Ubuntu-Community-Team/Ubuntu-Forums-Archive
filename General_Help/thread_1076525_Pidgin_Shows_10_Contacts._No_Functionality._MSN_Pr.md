---
title: "Pidgin Shows 1/0 Contacts. No Functionality. MSN Protocol."
date: 2009-02-21
forum: General Help
---

### Post by TroyDowling on 2009-02-21
Hello,

With the release of Intrepid a little while ago I eagerly jumped on the new release as soon as possible. I found it the best distro yet aside from one nagging detail. My favourite messaging client, Pidgin, did not work! At first I wrote this off as a bug in the program. However, I started to look into it in more detail...

[list]
[*] I downloaded the image of Ubuntu four times in total at different times (weeks in between)
[*] I burnt the image to a CD twice, two different computers. And to a DVD twice, same two different computers.
[*] All four of these disks checked out perfectly when booted up and MD5'd at the LiveBoot splash.
[*] All four disks installed properly WITH Pidgin working perfectly on my buddie's Alienware Laptop but not my Desktop nor Laptop.
[*] Pidgin DOES in fact work fine when I LiveBoot the disks, but as soon as I boot the OS off my hard disk I get the problem.
[*] It should be noted that when I sign into Pidgin, the MSN servers must recognize this because other clients like aMSN or Kopete get logged off.
[/list]

All four disks resulted in ME having the exact same problem with Pidgin. When I open it, the program runs fine, I make my MSN Account, but when it signs in it shows nothing aside from "Friends 1/0". There are no contacts whatsoever nor my custom groups (Friends and Family). This issue happens on BOTH my desktop system and my laptop, but NOT my friend's computer... I just don't get it. Any help would be appreciated because I'm not a fan of any of the other clients I've tried.

Attached is a screenshot of the contacts window. Also, the debug output is extremely long so I wont post that unless explicitly asked to. It also contains my entire address book and such so editing it all out would be a pain in the **** for me. Instead, I picked out the only lines in the whole thing that indicate in any way an issue. They are:

```

(10:29:00) dns: Wait for DNS child 14642 failed: No child processes
(10:29:00) dns: Wait for DNS child 14641 failed: No child processes
(10:29:01) gnutls: receive failed: A TLS packet with unexpected length was received.

```

Thanks,
Troy.

---

### Post by khc on 2009-02-24
I am quite sure you are not using pidgin that comes with the Ubuntu release, since gnutls is enabled. This is a known gnutls compatibility problem and the Ubuntu pidgin package is configured to use nss, which doesn't have this problem.

---

### Post by TroyDowling on 2009-02-25
Well, that seems quite possible. You'll have to inform me what I'm doing wrong because like I said; I'm merely using the Ubuntu Install disks, Ubuntu Canada/Main Repositories or Pidgin source. All three sources yield the same results. Are you able to link me to where I could find the Pidgin source with NSS instead of GNUTLS?

Thanks.

---

### Post by TroyDowling on 2009-03-16
**_Solution_**:

So, I figured out what I was doing wrong. I guess I was going about the problem wrong. User 'khc' was correct is saying that the problem was due to GNUTLS being active. In a nutshell, to use the MSN and/or Google Talk protocols, you need to have SSL encryption capability. This is done through one of two ways. Using the GNUTLS package or the Mozilla NSS package. On Ubuntu (which releases?), the GNUTLS package causes weird and seemingly unpredictable faults. Mine manifested as this weird contact list problem. So, you need to turn GNUTLS off and NSS on at the compile. This was really simple. Here's what I did:

1)

Completely remove all the old pidgin packages. I had some plugins and other packages that you may or may not have installed.

```

sudo aptitude purge libpurple-bin libpurple-dev libpurple0 pidgin pidgin-data pidgin-dbg pidgin-dev pidgin-extprefs pidgin-festival pidgin-libnotify pidgin-musictracker pidgin-plugin-pack pidgin-themes

```

2)

(Optional?) I noticed I still had some residual pidgin packages laying around in /usr/local/bin so I decided to move them into a folder on my desktop for the time being. Turns out I didn't need them as the new installation replaced them with new versions. So, either delete or move these elsewhere.

```

cd /usr/local/bin
sudo mkdir old_pidgin_backup
sudo mv finch pidgin purple-* ./old_pidgin_backup/

```

3)

Download the latest Pidgin source tarball from [here](http://www.pidgin.im/download/source/)

4)

Extract, configure (with NSS on, and GNUTLS off), make, and install

```

tar xvf pidgin-(VERSION).tar.bz2
cd pidgin-(VERSION)
./configure --enable-nss=yes --enable-gnutls=no
make
sudo make install

```

Notice the third command, this is telling pidgin to compile WITHOUT support for GNUTLS and WITH support for NSS. If you don't have either of these, pidgin should still compile, but you won't be able to use the MSN or GTalk protocols. These two configuration options and all the other accepted arguments are available in the 'INSTALL' file that came in the source tarball under the section "Optional Features".

Now pidgin should be installed and functioning for you! Thanks again to those who helped me recognize the problem.

Troy.

---

### Post by khc on 2009-03-18
Ubuntu's pidgin package uses nss, you were probably using your self-compiled pidgin from /usr/local

---

### Post by TroyDowling on 2009-03-18
I'm sure that's a possibility, but Pidgin did identify itself as 'pidgin-#.##-ubuntu' or something like that. In any regard, my solution still stands, does it not?

---

