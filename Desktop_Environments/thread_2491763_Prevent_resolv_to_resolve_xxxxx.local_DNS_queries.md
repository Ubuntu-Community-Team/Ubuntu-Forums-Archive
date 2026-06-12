---
title: "Prevent resolv to resolve xxxxx.local DNS queries"
date: 2023-10-19
forum: Desktop Environments
---

### Post by GonZo on 2023-10-19
Our private DNS server has a lot of domains under xxxx.mycompany.local domains which correspond to our internal IP addresses.

We're moving some developrs machines to Ubuntu and found that resolv service is failing to resolve those addesses despite others private xxx.mycompany.com only available in our internal DNS server work, so is able to connect to our private DNS server. Here you have a sample

[FONT=Courier New]$ nslookup onehost.mycompany.local
Server:		127.0.0.53
Address:	127.0.0.53#53

** server can't find onehost.mycompany.local: SERVFAIL

$ nslookup myhost.mycompany.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	myhost.mycompany.com
Address: 192.168.x.y[/FONT]

Other OSs( win mac) are able to solve dNS query, so I understand Ubuntu 22.04 manages .local domains in other way. 
Is there any way to force resolv use ALWAYS the dns server (at least for .local domains). I'm looking for the less traumatic solutions that avoid complicated configuration on every machine.

Regards

---

### Post by TheFu on 2023-10-19
Just a guess. I didn't test.  modify the /etc/nsswitch.conf DNS line.
Remove *mdns* and *mdns4_minimal*  ensure DNS is before [NOTFOUND=return] in the line.

This is just a guess.  It will prevent all mdns (as used by zeroconf and avahi) from working.  There are impacts to other easy-to-use network services like printers and certain media players if you do this.

BTW, whenever posting text files or terminal output, please use the 'code-tags' wrapper on the Adv Editor (or do it manually) so things line up and are clearer. No need to change fonts.

The local DNS caching is being done by systemd-resolved.  If you run a local DNS on your LAN, perhaps a pi-hole systems, then there's little reason to have systemd-resolved at all. Same for resolvconf (the older package).  Just manually add the 2 primary/backup DNS IPs to your /etc/resolv.conf file.  Be certain those other daemons are disabled and will not start again. I break the symlink and create a new resolv.conf file in addition.

---

### Post by GonZo on 2023-10-20
Thanks for your kindly help

I agree with you that multicastDNS is the problem here with .local domains, so I  tried to disable it chanight /etc/nsswitch.conf as follows

```
#hosts:          files mdns4_minimal [NOTFOUND=return] dns
hosts:          files dns [NOTFOUND=return] 
```
... but it didn't worked. Maybe because my OVPN connection is interfering in some way.

I "fixed" it removing the link of /etc/resolve.conf and replacing it with a file with same content but preceed with our private dns server

```
nameserver 192.168.xxx.xxx
nameserver 127.0.0.53
options edns0 trust-ad
search .

```
...which is exactly the kind of solution that I'm trying to avoid.

Anyway, it seems that using .local domains for our interferes with mDNS protocol, so the best solution in the long run it's simply avoid using them. So we start moving our .local domains to the recommended registered top level domains for private hosts as [RFC on mDNS recommends]("https://www.rfc-editor.org/rfc/rfc6762#appendix-G"). The next ones:

      .intranet.
      .internal.
      .private.
      .corp.
      .home.
      .lan.

The problem is fixed now and for the future. No configuration has to be done in any of the new machines. (we still keep the old .local registers in our DNS server but just to prevent)

My recommendation is to stop using .local domains for those issues.

Regards

---

### Post by TheFu on 2023-10-20
If you don't prevent systemd-resolved from running, that file will be overwritten multiple times a day (or at least at boot).  And if you prevent systemd-resolved from running, there's no need for the localhost nameserver, since it won't be running anyway.

1) create a new /etc/resolv.conf.new with the settings you want inside. Use

 ```
sudoedit /etc/resolv.conf.new

```
Add lines like this:
```
  nameserver 172.22.22.80
  nameserver 172.22.22.81
  search example.foo example.com
  domain example.foo
```
Obviously, [COLOR="#FF0000"][B]use your domains and IPs
[/B][/COLOR], not my examples.
2) run these commands, in order, **relatively quickly**:
```
  sudo systemctl stop systemd-resolved
  sudo rm /etc/resolv.conf
  sudo mv /etc/resolv.conf.new /etc/resolv.conf
  sudo chmod 644 /etc/resolv.conf
  sudo systemctl disable systemd-resolved
  sudo systemctl mask systemd-resolved

```That's the minimal. If you like, you can purge the systemd-resolved package or not.  They need to be run quickly because sudo uses name resolution to look up if your userid has the privilege. If done too slowly, say over 5 seconds, some of the later commands might fail and your userid will lose sudo-ability.

resolv.conf changes are immediate. No need to restart anything.
The good news is that these commands are exactly the same for any systemd system, so automation is really easy. I use ansible, but a remote ssh script into each system can make quick work of it too.

---

### Post by GonZo on 2023-10-20
As far I experimented, this should work fine. I suggest running all the commands in one line (concatenate with &&) to ensure is done fast.

But I will suggest this only if you're not able to move .local domains. Remember, a shortcut today can be huge problem tomorrow.

Again, thanks for your help.

---

### Post by TheFu on 2023-10-20
mdns taking .local has been around a long time - over 10 yrs.  OTOH, we each live in our own worlds and don't always see outside it.  I've been running DNS since the mid-1990s at work.  I always preferred the .lan TLD at work, but at home, I have a little more fun.

The changes above happen 1 time per install and are included in any backups, so it isn't a huge problem tomorrow if the network admin is consistent.  Until recently, it was trivial to select/paste multiple lines into a bash shell to have them done back to back.  There is a bash fix to get the old behavior back **set enable-bracketed-paste off **, but people new to Linux are often worried about changing their environment from the default (which is a good idea to be afraid).  

Often, I'm consistently wrong, but at least I'm consistent.  That makes any fixes quick, since they can be scripted as well.  One of my first Ansible scripts was to push specific /etc/hosts files out to each system here using j2 templating.  That was a good way to easily learn Ansible and to see the possibilities of power it can provide for system management.  I used that test for other devops tools as well and all the others made it much to hard to accomplish. Writing a custom ssh remote script is easier and how we did devops before marketing gave it a name.  

Heck, some people still use clusterssh for quick changes across many systems. I used that before Ansible for quick needs, but it trains an admin to be very careful about paths and commands, since different systems can have different locations for files, even if they are in the same relative location from a known point, like $HOME.

---

