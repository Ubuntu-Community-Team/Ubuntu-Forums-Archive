---
title: "Remote Desktop - Same session"
date: 2022-11-09
forum: Desktop Environments
---

### Post by frijole2 on 2022-11-09
Hi.  I have a specific use case that I'm trying to address in the best, most 'buntu way:
I often work from both home and the office.  I have a business VPN at the office so that's taken care of (OpenVPN).

[LIST]
[*]Remote access solution with the same session as I used at the console
[*]**I'd like to be able to pick up where I left off **when I'm at home **without re-logging in/out etc**. (_All my programs running right where I left off_)
[*]When I'm not at the office, I need for my console (monitor/keyboard/mouse physically attached to the computer) to be locked and desktop not shown for obvious reasons.
[*]Hopefully support a different resolution/screen geometry remotely.
[*]I'm willing to use a flavor of 'buntu that offers the best support/least resistance.
[/LIST]

I'm sick of Windows.  Once I resolve this use case, I can finally make the migration to Linux.
While I appreciate alternative use suggestions, they will not work for me.  I need this specific use case met. (ahem, TheFu :P)

Many thanks in advance.
-f

---

### Post by TheFu on 2022-11-10
Use 'x2go' both at home and work.  The session is virtual, so it won't show what's on the physical screen at home, but using x2go, you can connect to existing sessions and take over.

There's also a view-only method to connect for multiple other people, if you want to provide training views.

Start with reading this: [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

Plus, x2go is 2-3x faster than VNC or RDP, while using ssh for tunneling and credentials.  But your work network needs to allow ssh outbound connections, which I truly hope they aren't that dumb to allow.  Be certain to have your home router perform port-translation, say from 61022/tcp in to 22/tcp on your x2go-server.  x2go uses the same ssh connection that ssh, scp, sftp, rsync, and 50 other ssh-based tools leverage.  

This means that you'll need to get ssh working between where you are and home as well.  No way around that. Best of all, no blind trust in some 3rd party remote-desktop middle-man server is needed.

After all, ssh is how all computers get secure and convenient connections for almost any use.  
> ssh is enough for
    secure remote access to files via sftp
    secure remote filesystem access via sshfs
    secure remote CLI/shell access to systems with plain ssh
    secure remote desktops via x2go/freenx
    secure remote file replication with rsync (ssh is the default rsync protocol)
    secure port forwarding of selected TCP ports (good as a SOCKS5 proxy)
    secure remote editing with vim/gvim and other editors
    pseudo-VPN with sshuttle
    

The term "console" means something pretty specific in Unix.  It is a text-only thing, but if I'm understanding correctly, you want a remote GUI desktop.  I've used x2go as stated above and reconnected to the virtual GUI session from many different locations.  I used it when I was programming and had 15 windows setup exactly as I needed them across 6 workspaces.  Getting all of that setup, the right files open to the right places took about 15 minutes. I understand completely why reconnecting exactly to the same desktop is useful.  The problem is that x2go has to be used on both systems to connect into the virtual session. There's no way to use the physical session that is displayed on the screen that I'm aware. Sorry.  That would be a huge security failure, since having the screen mirrored when you aren't there would beg for someone else to walk up and screw with the unlocked system.

For text sessions over ssh, there's tmux or screen, but those don't do GUI stuff. Probably not what you seek.

If you are really using a 'console' session, then for about $250, you can get a pikvm to provide 100% remote access, including a power on/off, full BIOS access and 1080@60Hz remote access completely regardless of the OS on the remote system.  [https://youtu.be/232opnNPGNo](https://youtu.be/232opnNPGNo) probably explains it better than I can.

---

### Post by ActionParsnip on 2022-11-10
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by frijole2 on 2022-11-10
Hundreds of browser tabs, multiple terminal windows doing various things (including ssh to many systems), vs code, various documents opened with changes mid sentence, several email responses, etc.
The tear down/setup of everything i have running is a non-trivial task.  reboots for updates are my nemesis.  logging in/out to facilitate location shifting is out of the question.
RDP in Windows facilitates this use case beautifully.  I'm just looking for a close facsimile in Linux.

---

### Post by frijole2 on 2022-11-10
> **TheFu said:**
> Plus, x2go is 2-3x faster than VNC or RDP
I can watch youtube through RDP on windows from remote with a 10mbps uplink.  X2go is a slide show.

> **TheFu said:**
> [COLOR=#000000]There's no way to use the physical session that is displayed on the screen that I'm aware. [/COLOR]
That's what I was pretty sure of before I created this thread.  I was hoping I was overlooking something.
...well you can with Gnome screen sharing, but in their brilliance, they left the [s]console[/s] local display unlocked
which as you mentioned:  > **TheFu said:**
> [COLOR=#000000]There's no way to use the physical session that is displayed on the screen that I'm aware. Sorry. That would be a huge security failure, since having the screen mirrored when you aren't there would beg for someone else to walk up and screw with the unlocked system.[/COLOR]
EDIT:
It's worse than that.  I forgot to mention that if the local display is locked, you can't even connect.

see screedshot:
[https://imgur.com/a/SJQSXIf](https://imgur.com/a/SJQSXIf)

Surely I'm in the wrong for doing things the wrong way and being a bad person who has ever used Windows.  I was lured by the sexy siren song of Windows RDP way back in 2000, and have never been able to escape her.

---

### Post by TheFu on 2022-11-10
We all have different backgrounds and experiences.  Using Windows doesn't make someone bad.  We each have different needs and nobody knows everything about all OSes, networking, security, and risk management.

> I can watch youtube through RDP on windows from remote with a 10mbps uplink. X2go is a slide show.
My connections over the internet run between 30Mbps and 128Kbps ISDN.  x2go **can** do video and the bandwidth to be used can be tweaked in the settings along with the compression levels, so that even with poor networking, video can be watched.  It is usually better in my situation to setup a SOCKS proxy over ssh to the video server, then limit the stream bandwidth to the browser by controlling the bitrate/resolution of the video, but perhaps everyone doesn't think like I do.

On my home Gbps LAN, sometimes I forget that I'm using x2go and will watch some video.  I also use some other methods for remote sessions, but didn't feel they'd be a good idea over the internet.  Tweaking the bandwidth and compression settings a tiny bit can make x2go awesome when RDP sucks.  I've actually used x2go into a system on the LAN, then started an RDP session into a Windows system on the same LAN to do simple work remotely that would be impossible with RDP directly.  But lots of people wouldn't even consider something like that.

Most people here don't have a VPN between the systems, so RDP really isn't an option without an ssh-tunnel too.  RDP is famous for having terrible security.  There are large numbers of Windows RDP connections hacked daily.  A secured VPN mitigates that issue.  Gnome stuff - that's a completely different issue that I won't touch.
 
But if you've been happy with RDP and feel the risks have been mitigated for your situation, go with whatever option works for you. Hopefully, you won't be burned.

> It's worse than that. I forgot to mention that if the local display is locked, you can't even connect.
BTW, x2go doesn't care what the local session on the desktop is doing. Locked or not.  The remote session is possible and can be accessed from different clients regardless of whether a local GUI session on the physical system is running or not.  But it seems x2go doesn't fit the idea you have for a solution.  That's fine too.

You didn't say anything about the PIKVM option or did I miss that?

---

### Post by frijole2 on 2022-11-11
> **TheFu said:**
> You didn't say anything about the PIKVM option or did I miss that?
Same problem.  In order to use that, your local display has to be unlocked.  Nevermind the resolution/screen geometry issues.
It might sound disgusting, but Windows RDP is glorious near perfection.  I can connect remotely with more or less monitors, larger, or smaller resolutions, any combination.  Too bad the rest of the system has it's various and sundry... issues.

I don't want to use Windows... but it's the only remote desktop connection that is sane.  Everything on Linux is a patchwork of insecure partial solutions that end up in a Venn diagram with no overlap.
I just find it strange that in the 22 years that Windows has had Remote Desktop, nothing on Linux has replicated its secure functionality.

---

### Post by TheFu on 2022-11-11
> **frijole2 said:**
>  
I just find it strange that in the 22 years that Windows has had Remote Desktop, nothing on Linux has replicated its secure functionality.

RDP isn't secure for huge numbers of installs.  I say this based on all the press coverage of the RDP hacks in the news the last 20+ yrs.  It is hacked all the time unless some other VPN/tunnel is used to protect it.  

Perhaps there is mitigation that isn't just using a VPN.

I'd hope that a $200B company with their software running on 2 systems can get them connected.  It would be amazing if those connections were secure too, but that has proven to be very difficult.  Perhaps your setup is the exception?  [https://www.makeuseof.com/how-can-remote-desktop-protocol-be-hacked/](https://www.makeuseof.com/how-can-remote-desktop-protocol-be-hacked/)  I'm not too impressed by the writer of that article, but felt using a website you've likely heard of verses all the blogs by security professionals was more important.  The security professional blogs show multiple different techniques to crack into RDP.

I'm confused by the complaints about resolutions.  Just set the resolution to what you want. I'm positive that works with x2go. I know it works with SPICE too, but SPICE isn't available on physical installs, just virtual machines.  I don't have a 4K monitor, but do run at 1920x1200 most of the time, unless I'm using a laptop, mine are 1920x1080, sadly. I always feel like I'm missing 200px vertically.  Maybe Santa will bring a 4k monitor here? ;)

As for the PIKVM, the screen doesn't need to previously be unlocked.  To the remote computer, it is like someone is using the local mouse and the local keyboard. If it is locked, type in the password and unlock it.  But anyone walking passed could sit at the computer and either watch what's happening or unplug the remote connection and have their way.  I'd probably put the computer in a secure location and turn off the monitor before leaving for the day.

We seem to be going in circles. Maybe others will have better options and post.

---

### Post by frijole2 on 2022-11-11
> **TheFu said:**
> Perhaps there is mitigation that isn't just using a VPN.
I acknowledge that the RDP network protocol has vulnerabilities.  But we've known that for 20 years.  We have a number of tools to deal with that: (VPN, 802.1X, etc.) 

> **TheFu said:**
> I'm confused by the complaints about resolutions.  Just set the resolution to what you want. I'm positive that works with x2go. I know it works with SPICE too, but SPICE isn't available on physical installs, just virtual machines.  I don't have a 4K monitor, but do run at 1920x1200 most of the time, unless I'm using a laptop, mine are 1920x1080, sadly. I always feel like I'm missing 200px vertically.  Maybe Santa will bring a 4k monitor here? ;)
It's easy to understand.  The resolution and screen geometry I have on my Linux workstation at work doesn't match what I have at home.  At work I have 2x 1920x1200 displays.  At home I have a single 2560x1440 monitor.  My laptop (which I use to connect to work as well) has a single 1920x1080 display.

When you connect to a Linux local desktop remotely, the desktop and window resolutions don't adapt to the remote system; something that Windows does fairly well (at least since Windows 10).

> **TheFu said:**
> As for the PIKVM, the screen doesn't need to previously be unlocked.  To the remote computer, it is like someone is using the local mouse and the local keyboard. If it is locked, type in the password and unlock it.  But anyone walking passed could sit at the computer and either watch what's happening or unplug the remote connection and have their way.  I'd probably put the computer in a secure location and turn off the monitor before leaving for the day.
Well yeah, I don't really want a coworker looking at what I'm doing if they decide to turn on a monitor, or maybe hijack my workstation by unplugging the network from the PiKVM mid use (after I'm logged into all my admin stuff).  And while I should be able to trust my coworkers, and have a secure environment for my system, etc.. that's a lack of security even wider than the shortcomings in the RDP protocol.

Yeah I agree we're getting nowhere other than venting.  Maybe some GNOME dev might see this and understand the shortcomings of their screen sharing (or even explain a use case for it as it currently exists lol).

---

