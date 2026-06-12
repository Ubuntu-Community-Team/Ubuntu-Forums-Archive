---
title: "Trying to setup remote GUI interface"
date: 2021-11-02
forum: Desktop Environments
---

### Post by RonRN18 on 2021-11-02
I have many different iterations of Ubuntu servers running, with nearly all of them in VM environments. I don't have much experience in the GUI environment and needing to create a VM (XCP-ng) running a desktop setup. As it is a VM, there is no native display, but I would like to use either a VNC or RDP client to access this VM. I seem to keep running into issues. In several different tutorials I've seen, it talks about going into the Settings->Sharing menu to enable Screen Sharing... the problem is that this is NOT listed as an option. Whereas in all of the tutorials I've seen, Under the "Computer Name" bit, there are two sections that can be enabled or disabled, "Screen Sharing" and "Remote Login", but in my case, I have "Media Sharing" and "Remote Login". Why am I NOT seeing "Screen Sharing" and how can it be enabled? Is there a major difference between using VNC vs RDP? I just wish to run a Linux-based GUI app from my laptop.

---

### Post by ActionParsnip on 2021-11-02
What are you wanting to do on the remote system that needs the full desktop session? Why set this up at all? Let's say you get this setup and you can get a desktop session, what will you do once connected?

There may be a sleeker solution to what you want to achieve.

---

### Post by TheFu on 2021-11-02
Forget vnc or rdp.

Use x2go.  There is a PPA, but it shouldn't be necessary.  Also, don't attempt to use Gnome3+ DEs. That means you need to install any of the lighter DEs - Mate, XFCE, KDE, LXQt ... any of the ubuntu flavors will work with x2go too ... just not the default which uses Gnome3 or Gnome4. 

Also, with KVM as the VM host, you can use virt-viewer with the SPICE protocol. I've posted the exact commands that work with libvirt/KVM systems here a number of times, but the guest VM has to be setup to QXL and SPICE as the display protocols. That should be the default in any modern Ubuntu KVM/libvirt release.

VNC and RDP just suck in comparison.  I get the feeling that the "official" Gnome Desktop sharing only works for the Gnome dev team.

I'm fairly certain I've posted steps to use x2go and SPICE/Qxl in these forums a few times.  Those instructions haven't changed that I'm aware, but to be honest, I haven't used x2go since COVID and we stopped traveling.  Before that time, x2go was the only way I'd access remote desktops - I've done that from 5 continents.  X2go is based off NX protocol which is uses ssh for the network security aspects. That means ssh is the only external port needed to be open, and all the typical ssh authentication/security stuff works with it.  That includes ssh-keys/-certs and the ~/.ssh/config file are fully honored, at least for Unix-based desktop running x2goclient.

On the same LAN, I use SPICE.  Linux desktops all seem to have the QXL virtual GPU driver loaded. There is a QXL driver for Windows guests which works well too. Alas, security on the LAN is just as bad as for VNC/RDP, which is why using SPICE over the internet requires a full VPN layer (setup outside this connectivity).  Spice knowledge is good, as RHEL uses it for all their oVirt VM access.  oVirt isn't ported to Ubuntu. Sorry.

If you just want to run an X/Windows application from your laptop, then why have a full desktop?  That's "Windows-think" and totally unnecessary.  Just run the app over an **ssh -X** connection.  It will be lighter on the remote system AND lighter on your Unix-based laptop.  I understand that MS-Windows has some sort of compatibility later these days.  If it doesn't provide an X/server, then it isn't compatible. Period.  If you are stuck on Windows from the laptop, then the best answer on the LAN is to use virt-viewer.exe and Spice or x2go.  If you want key-based ssh to work with x2go, you'll need to use the ssh-keygen provided with x2go, not the crap MSFT provides.  ssh has been around since about 1995, yet MSFT delayed support for it and the sftp/scp included protocols for 20 yrs. Then when they finally got around to it, they didn't include all the tools like ssh-copy-id.  Pfffft.  Sorry, I've just been disappointed too many times and that has continued.

```
$ ssh -X userid@remotecomputer  "command-gui -o option1 -p option2 file3"
```
is an example command. Put in your userid and remotecomputer as needed.  If ssh-key have been transferred already, you'll be asked to unlock the key only as often as your ssh-settings require. I think it is just once per login on the client. ssh-agent can be used to pass on ssh-keys to other systems. That can be very convenient, but isn't usually knowledge needed by most users.

That should be enough to get you started.

OTOH, if you are stuck wanting to use RDP or VNC, I cannot help.  After discovering that x2go was 2-3x faster, more convenient AND more secure, I never looked back.

---

