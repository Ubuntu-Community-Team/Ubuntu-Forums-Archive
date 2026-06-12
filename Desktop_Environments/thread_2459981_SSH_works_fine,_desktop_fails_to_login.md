---
title: "SSH works fine, desktop fails to login"
date: 2021-03-30
forum: Desktop Environments
---

### Post by hikariws on 2021-03-30
Hello friends!

I'm having an odd issue on my personal server. It runs Ubuntu 20.04.

Usually I only use it from SSH, it has a monitor connected but it's always turned off. Yesterday I used it to restore the partition backup from a few months ago so I'd upgrade softwares and install a few new then create a new backup, and I was unable to login.

It has the usual purple login screen showing my username. I click on it and the password input appears. But when I type my password it waits a second and the login screen comes back. I'm not sent to desktop.

I was still able to do what I wanted because top right icons are working and I was able to reboot from there, but I'm now unable to login locally. Even after the restore, the same issue remained.

SSH continues to work as always. I'm able to open remote windows from scite, gnome-system-monitor, pcmanfm using PuttY + Xming. Apache and its Pihole WebUI also works. Tor, Nyx, etc, all working. Only the local GUI desktop doesn't login.

There's also a popup that keeps repeat showing very quickly from a fraction of second. I managed to read it: "activation of network connection failed". I guess it's not related.

How can I fix it? I stay months without using it locally, but some time I may need to.

---

### Post by CatKiller on 2021-03-30
> **hikariws said:**
> But when I type my password it waits a second and the login screen comes back.

The specific symptom is that your desktop session is crashing immediately, which is why you get the login screen again: the first thing that you get when the desktop manager restarts.

Graphics driver would be a likely culprit. It might be some other setting, though. Trying to log in as another user would be a useful troubleshooting step, as would consulting the logs.

---

### Post by TheFu on 2021-03-30
change to a different tty, then
[LIST=1]
[*]login
[*]sudo apt update
[*]sudo apt full-upgrade
[*]sudo ubuntu-drivers autoinstall
[/LIST]

---

### Post by hikariws on 2021-03-30
tnx for the help!

> **TheFu said:**
> change to a different tty, then
[LIST=1]
[*]login
[*]sudo apt update
[*]sudo apt full-upgrade
[*]sudo ubuntu-drivers autoinstall
[/LIST]


That didn't work :/ "No drivers found for installation."

I created a new user and it was immediately detected and got a new entry to the login screen. I logged and same issue happened.

---

### Post by The Cog on 2021-03-31
I think I remember this can happen if you have run some graphical apps as root at some point. Try a tty console or ssh login, remove any Xauthority file, and chown any root-owned files back to yourself.

---

### Post by TheFu on 2021-03-31
I haven't a clue, but perhaps reinstalling the login manager will help? Which should be used depends on the WM/DE installed. I use lightdm on my WM-only setups.

The networking issue could be caused by the change from ifupdown to netplan.  On the tty, do DNS and WAN pings work?

The Cog's idea is good too. I've seen GUI logins fail because someone used **sudo gedit** very early in their GUI setup process. This created .config and some subdirectories and files with root ownership.  If the gnome-DB is owned by root, but in your HOME, GUI logins can be blocked. The fact that non-GUI tty logins still work says this is a GUI issue.  I'm a little concerned that creating a new user then logging in with that user account isn't working. That makes no sense.

---

### Post by hikariws on 2021-03-31
> On the tty, do DNS and WAN pings work?

It's the DNS server. By WAN do u mean local network adapter, or router's WAN? Internet is working.

> I think I remember this can happen if you have run some graphical apps as root at some point. Try a tty console or ssh login, remove any Xauthority file, and chown any root-owned files back to yourself.


Indeed, I have a Xauthority setting so I'm able to run sudo GUI apps over PuttY, specially scite. I could remove it to see if it's the cause, but I need it active.

What's the best way to do it? I'm also concerned that it seems harder to solve than I expected.

---

### Post by TheFu on 2021-03-31
> **hikariws said:**
> It's the DNS server. By WAN do u mean local network adapter, or router's WAN? Internet is working.

Indeed, I have a Xauthority setting so I'm able to run sudo GUI apps over PuttY, specially scite. I could remove it to see if it's the cause, but I need it active.

What's the best way to do it? I'm also concerned that it seems harder to solve than I expected.

```
sudo -H {name-of-program}
```

Can your system ping 1.1.1.1 AND google.com?  There's some sort of networking issue at some point. For some setups, DNS needs to work to resolve the hostname. If that fails, then authentication for different needs fails.  A local login shouldn't fail, but if there are LDAP/AD accounts, those could fail if the credentials aren't cached.

I always found running putty + some X/server problematic. The solution I ended up with was to run a small Linux VM and use the normal X/Server for all remote access needs.  Of course, the other solution is to purchase a commercial X/Server which supports a broader range of needs than the Windows ports.  I think the best X/Servers consolidated into just a few companies. They were ~ $200 when I last used them in the early 2000s.  So ... I really don't know anything.  From around 2010 - 2015, I used NX clients from Windows to connect into full desktops on Linux.  Started with FreeNX, but it wasn't all that stable. Didn't like NoMachine's limitations, then found x2go and switched. Ran with that for a few years. It was very stable from Windows and from Linux workstations. I still use it when traveling, but inside the LAN, I'm on Linux workstations pretty much by default.

---

### Post by CatKiller on 2021-03-31
> **hikariws said:**
> I created a new user and it was immediately detected and got a new entry to the login screen. I logged and same issue happened.

Sounds like graphics driver/configuration issue, then. You've not said what hardware you're using.

---

### Post by ActionParsnip on 2021-03-31
Make sure there is free space and that the user is the owner of it's own $HOME

---

### Post by hikariws on 2021-03-31
> **TheFu said:**
> ```
sudo -H {name-of-program}
```

Can your system ping 1.1.1.1 AND google.com?  There's some sort of networking issue at some point. For some setups, DNS needs to work to resolve the hostname. If that fails, then authentication for different needs fails.  A local login shouldn't fail, but if there are LDAP/AD accounts, those could fail if the credentials aren't cached.

I always found running putty + some X/server problematic. The solution I ended up with was to run a small Linux VM and use the normal X/Server for all remote access needs.  Of course, the other solution is to purchase a commercial X/Server which supports a broader range of needs than the Windows ports.  I think the best X/Servers consolidated into just a few companies. They were ~ $200 when I last used them in the early 2000s.  So ... I really don't know anything.  From around 2010 - 2015, I used NX clients from Windows to connect into full desktops on Linux.  Started with FreeNX, but it wasn't all that stable. Didn't like NoMachine's limitations, then found x2go and switched. Ran with that for a few years. It was very stable from Windows and from Linux workstations. I still use it when traveling, but inside the LAN, I'm on Linux workstations pretty much by default.

Indeed, I just tested and domain resolving is failing, ping: google.com: Temporary failure in name resolution

That's odd from the server where Pihole is running. I tried on Win10 and resolving worked.

There's only 1 file on /etc/netplan/:

```
network:  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp6: yes
      dhcp4: no
      addresses: [192.168.49.4/24]
      gateway4: 192.168.49.1
      nameservers:
        addresses: [192.168.49.4]
```

It points to use itself as DNS server, is there anything wrong?

Anyway, I rebooted it and now it's resolving again.

What should I do with sudo -H?

I have some VMs and even use OpenWRT to route their vmnet instead of Vmware's NAT. But I have my server on my normal use and I'd lose usability if I'd confine its access to a VM, specially monitoring CrashPlan. It's not good to remove a feature I use all the time for one I rarely use.

> Make sure there is free space and that the user is the owner of it's own $HOME

I verified and /home/username is owned by it, same for all files inside it, including /home/username/.Xauthority.

Same goes for the testing user I created yesterday.


> Sounds like graphics driver/configuration issue, then. You've not said what hardware you're using.

Sorry, it's a Intel i5-10400, 32GB RAM, Asus TUF GAMING B460M-PLUS. Video uses CPU's IGP.

---

### Post by CatKiller on 2021-03-31
> **hikariws said:**
> Sorry, it's a Intel i5-10400, 32GB RAM, Asus TUF GAMING B460M-PLUS. Video uses CPU's IGP.
There's been a couple of threads recently about people having trouble lately with newer Intel integrated graphics, but they don't seem to have found a resolution (one put in a dedicated GPU and the problem went away, and the other one's still open AFAIK). Might be related, might not.

So the next step is to check your logs to see what's having the problem. You've established that it's not a *user* configuration issue, since the fresh user had the same symptom, but it could still be a *default* configuration issue of some kind, and on the system side you've got the driver as part of the kernel, whatever firmware needs to be loaded, and Mesa turning graphics calls into driver calls. Issues with those should show up in the logs. 

Whichever you're using out of X and Wayland, trying the other one would probably be a thing to try as well.

---

### Post by hikariws on 2021-03-31
Sorry I didn't understand part of what you said, about Mesa, Wayland. I don't remember installing any driver manually, They were installed automatically when Ubuntu was installed and/or some upgrade.

What logs must I look?

If it's a driver issue related to Comet Lake, then I'll just wait new drivers arrive and update. But I was able to login in the past.

---

### Post by CatKiller on 2021-03-31
> **hikariws said:**
> Sorry I didn't understand part of what you said, about Mesa, Wayland.  

Wayland is the replacement for X. They both provide the graphical environment. At the login screen you should have the option of which session you want to start. Otherwise I think there's a GDM option (assuming you're trying to use Gnome) somewhere. 

Mesa is the userland part of the open source graphics drivers. Applications talk to Mesa, Mesa talks to the kernel, and the kernel talks to the hardware. *Sometimes* a new version of Mesa is needed for new hardware, but that's not the case here since yours used to work. Bugs in Mesa could still cause you issues, though. 

> I don't remember installing any driver manually, They were installed automatically when Ubuntu was installed and/or some upgrade. 

That's right. The Intel drivers are open source, so they're already included in the kernel and Mesa. There's also (optional, I think?) proprietary firmware that does some stuff. 

We don't know what's changed on your machine between it working and it not. It sounds like you don't, either. So we trace through and try to find out what isn't doing the right thing. 

> What logs must I look?

The usual places. dmesg for kernel messages, /var/log/Xorg.0.log for X, wherever Wayland stores its log if it's somewhere different (I've got Nvidia hardware, so I've never used it), systemd keeps logs somewhere, Gnome and GDM probably keep logs somewhere. You're trying to establish which part of the stack is causing your desktop session to crash so that you can fix it.

---

### Post by TheFu on 2021-03-31
I'm a little worried that there are network issues
and
there is pihole
there is virtualization
there is ddwrt
there is DHCP for IPv6, but not IPv4
DNS isn't working ... on the same machine.

My VM hosts have bridges for VMs to connect or they have a NIC passed through for any router VMs.  I don't want the hostOS to see the traffic meant for any WAN router.  A LAN router has lots of wiggle room - since the traffic it handles has been drastically filtered and doesn't hold any evil internet stuff.

But perhaps I'm not understanding the setup.

---

### Post by hikariws on 2021-03-31
@CatKiller tnx for the patience :) I didn't know there was a replacement for X!

There's no folder or file starting with /var/log/X*:

```

drwxrwxr-x  22 root              syslog               4096 mar 31 14:17 ./
drwxr-xr-x  15 root              root                 4096 dez 27 22:32 ../
-rw-r--r--   1 root              root                 4617 mar 31 00:39 alternatives.log
-rw-r--r--   1 root              root                  646 fev  5 11:21 alternatives.log.1
-rw-r--r--   1 root              root                  863 jan 20 06:46 alternatives.log.2.gz
-rw-r--r--   1 root              root                 3705 dez 29 19:20 alternatives.log.3.gz
drwxr-x---   2 root              adm                  4096 mar 31 00:00 apache2/
-rw-r-----   1 root              adm                 67364 mar 31 00:43 apport.log
-rw-r-----   1 root              adm                145028 mar 30 23:59 apport.log.1
-rw-r-----   1 root              adm                   463 mar 29 21:56 apport.log.2.gz
-rw-r-----   1 root              adm                   425 dez 29 21:04 apport.log.3.gz
drwxr-xr-x   2 root              root                 4096 mar 31 14:18 apt/
-rw-r-----   1 syslog            adm                813514 mar 31 20:04 auth.log
-rw-r-----   1 syslog            adm                 11118 mar 29 21:44 auth.log.1
-rw-r-----   1 syslog            adm                  1911 fev 12 11:07 auth.log.2.gz
-rw-r-----   1 syslog            adm                 50946 fev  5 11:15 auth.log.3.gz
-rw-r-----   1 syslog            adm                  4925 jan 19 12:03 auth.log.4.gz
-rw-------   1 root              root                29306 mar 31 14:17 boot.log
-rw-------   1 root              root                34677 mar 30 00:00 boot.log.1
-rw-------   1 root              root                30593 mar 29 21:44 boot.log.2
-rw-------   1 root              root                29988 fev 12 11:07 boot.log.3
-rw-------   1 root              root                55906 fev  5 11:15 boot.log.4
-rw-------   1 root              root                88980 jan 21 00:00 boot.log.5
-rw-------   1 root              root                33023 jan 20 00:00 boot.log.6
-rw-------   1 root              root                38930 jan 19 12:03 boot.log.7
-rw-r--r--   1 root              root               104003 jul 31  2020 bootstrap.log
-rw-rw----   1 root              utmp                    0 mar 29 21:44 btmp
-rw-rw----   1 root              utmp                    0 fev  5 11:15 btmp.1
drwxr-xr-x   2 root              root                 4096 mar 31 00:00 cups/
drwxr-xr-x   2 root              root                 4096 jul 20  2020 dist-upgrade/
-rw-r--r--   1 root              adm                 94148 mar 31 14:17 dmesg
-rw-r--r--   1 root              adm                 94114 mar 29 22:32 dmesg.0
-rw-r--r--   1 root              adm                 22113 mar 29 21:44 dmesg.1.gz
-rw-r--r--   1 root              adm                 23081 fev 12 11:07 dmesg.2.gz
-rw-r--r--   1 root              adm                 23029 fev  5 20:23 dmesg.3.gz
-rw-r--r--   1 root              adm                 23144 fev  5 11:15 dmesg.4.gz
drwxr-xr-x   2 _dnscrypt-proxy   nogroup              4096 fev 12 11:12 dnscrypt-proxy/
-rw-r--r--   1 root              root               245326 mar 31 14:18 dpkg.log
-rw-r--r--   1 root              root                63639 fev 12 11:08 dpkg.log.1
-rw-r--r--   1 root              root                 6878 jan 20 22:42 dpkg.log.2.gz
-rw-r--r--   1 root              root               113782 dez 31 16:18 dpkg.log.3.gz
-rw-r--r--   1 root              root                32064 mar 31 00:44 faillog
-rw-r--r--   1 root              root                10974 dez 27 19:19 fontconfig.log
drwx--x--x   2 root              gdm                  4096 out  7  2019 gdm3/
-rw-r--r--   1 root              root                 1358 mar 31 14:17 gpu-manager.log
drwxr-xr-x   3 root              root                 4096 jul 31  2020 hp/
drwxr-xr-x   2 root              root                 4096 dez 27 17:52 installer/
drwxr-sr-x+  3 root              systemd-journal      4096 dez 27 18:05 journal/
-rw-r-----   1 syslog            adm                247115 mar 31 19:40 kern.log
-rw-r-----   1 syslog            adm                118034 mar 29 21:44 kern.log.1
-rw-r-----   1 syslog            adm                 44844 fev 12 11:07 kern.log.2.gz
-rw-r-----   1 syslog            adm                134376 fev  5 11:15 kern.log.3.gz
-rw-r-----   1 syslog            adm                 43276 jan 19 12:03 kern.log.4.gz
-rw-rw-r--   1 root              utmp               292584 mar 31 19:38 lastlog
drwxr-x---   2 www-data          www-data             4096 mar 30 00:00 lighttpd/
drwxr-xr-x   2 root              root                 4096 set  5  2019 openvpn/
drwxr-xr-x   2 pihole            pihole               4096 dez 28 14:35 pihole/
-rw-r--r--   1 root              pihole              95533 mar 30 09:37 pihole_debug.log
-rw-r--r--   1 pihole            pihole              20828 mar 31 19:59 pihole-FTL.log
-rw-r--r--   1 pihole            pihole            2527206 mar 31 00:00 pihole-FTL.log.1
-rw-r--r--   1 pihole            pihole              85962 mar 30 00:00 pihole-FTL.log.2.gz
-rw-r--r--   1 pihole            pihole               2377 mar 29 21:44 pihole-FTL.log.3.gz
-rw-r--r--   1 pihole            pihole            4368009 mar 31 20:04 pihole.log
-rw-r--r--   1 pihole            pihole           20076805 mar 31 14:17 pihole.log.1
-rw-r--r--   1 pihole            pihole            1923671 mar 31 00:00 pihole.log.2.gz
-rw-r--r--   1 pihole            pihole             213749 mar 30 00:00 pihole.log.3.gz
-rw-r--r--   1 pihole            pihole              66958 mar 29 21:44 pihole.log.4.gz
-rw-r--r--   1 pihole            pihole              22059 fev 12 11:07 pihole.log.5.gz
-rw-r--r--   1 root              root                 2224 jan  3 03:53 pihole_updateGravity.log
drwxrwxr-t   2 root              postgres             4096 mar 29 21:44 postgresql/
drwx------   2 root              root                 4096 jul 31  2020 private/
drwxr-x---   3 root              adm                  4096 mar 29 21:44 samba/
drwx------   2 speech-dispatcher root                 4096 jan 19  2020 speech-dispatcher/
-rw-r-----   1 syslog            adm             292908966 mar 31 20:04 syslog
-rw-r-----   1 syslog            adm             495100396 mar 31 00:00 syslog.1
-rw-r-----   1 syslog            adm               1330517 mar 30 00:00 syslog.2.gz
-rw-r-----   1 syslog            adm                127090 mar 29 21:44 syslog.3.gz
-rw-r-----   1 syslog            adm                312462 fev 12 11:07 syslog.4.gz
-rw-r-----   1 syslog            adm               3039951 fev  5 11:15 syslog.5.gz
-rw-r-----   1 syslog            adm               2410940 jan 21 00:00 syslog.6.gz
-rw-r-----   1 syslog            adm                297551 jan 20 00:00 syslog.7.gz
drwxr-xr-x   2 root              root                 4096 dez 23  2019 sysstat/
drwxr-s---   2 debian-tor        adm                  4096 mar 31 00:00 tor/
-rw-------   1 root              root                    0 jul 31  2020 ubuntu-advantage.log
drwxr-x---   2 root              adm                  4096 mar 31 00:00 unattended-upgrades/
-rw-rw-r--   1 root              utmp               140544 mar 31 19:38 wtmp

```

There's a file syslog on my home folder, but it hasn't changed since 2020-12-31.

@TheFu srsly what did u say?

---

### Post by TheFu on 2021-03-31
> **hikariws said:**
>  @TheFu srsly what did u say?

Think I said, the system seems very complex and that I didn't understand the setup. Feel free to ignore me.

---

### Post by CatKiller on 2021-03-31
> **hikariws said:**
> There's no folder or file starting with /var/log/X*:
Hey, you found where GDM keeps its logs.

Guess you were using Wayland before, then. You should be able to try not using Wayland, to see if it helps.

---

### Post by hikariws on 2021-04-02
> **TheFu said:**
> Think I said, the system seems very complex and that I didn't understand the setup. Feel free to ignore me.

Don't worry, I thought u were joking me because I wasn't understanding.

I restored backup again. Netplan was still using NetworkManager. It's failing to receive IPv6 global address for some reason. It's not a big issue but annoys me.

> **CatKiller said:**
> Hey, you found where GDM keeps its logs.

Guess you were using Wayland before, then. You should be able to try not using Wayland, to see if it helps.

/var/log/gdm3/ is empty.

How do I disable Wayland?

If it's so troubling, maybe I should just disable X autoloading and just leave terminal? I'd lose GUI but at least I could log for some troubleshooting, like losing network access.

---

### Post by deadflowr on 2021-04-02
> How do I disable Wayland?
Wayland is a login option.
When you select your username at the login screen, 
before you enter your password, click on the icon the pops up in the bottom right corner.
You can switch session types here.
On Ubuntu 20.04 it should show two options: Ubuntu and Ubuntu on Wayland.
Select Ubuntu and then you should be able to close the popup and enter your password.

---

### Post by hikariws on 2021-04-02
wow IT WORKED!! hahahaha I had lost hope alrdy!

I's Ubuntu by default. O changed to Ubuntu on Wayland and desktop loaded!

Does it help understand what the issue is?

---

### Post by CatKiller on 2021-04-02
> **hikariws said:**
> Does it help understand what the issue is?
Well, it means that your system is mostly OK, and X has some kind of issue.

Wayland is the future - development of X has already stopped, and Wayland-by-default is having another trial with 21.04 - so if Wayland works for you just stick with that.

---

### Post by deadflowr on 2021-04-02
Well, the Ubuntu option is legacy X11, so something is broken with that.
Perhaps similar issues as this bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1856846]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1856846")
I would guess the things to look at are, the dmesg and other log outputs and determine is any crash reports were generated in /var/crash.

---

### Post by hikariws on 2021-04-02
I looked on dmesg and nothing seems to relate to crash or X, /var/crash only has 1 file about notepadqq. Anyway, it's working on Wayland and is rarely used, so let it be.

tnx a lot for all the effort on helping me!

---

