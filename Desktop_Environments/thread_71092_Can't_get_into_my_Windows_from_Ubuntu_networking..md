---
title: "Can't get into my Windows from Ubuntu networking."
date: 2005-10-02
forum: Desktop Environments
---

### Post by Bandit614 on 2005-10-02
I have a Laptop with windows and a desktop with Ubuntu. They can ping eachother, and they recognize eachother. When I try to get into my laptop to transfer stuff, it asks for username, domain, and password. The laptops name is "samlaptop", and my username on the windows system is "Sam". I don't have it password protected, and I can't figure this all out.

Help please?

Also, I am really sorry if this is in the wrong section. I looked at the networking section, but they all seemed to be hardware related, and I don't think this is. Move if neccesary.

---

### Post by stoneguy on 2005-10-02
Sounds like you're trying to use your Ubuntu machine as a Samba server. It can be done, but it's not just pushing a button.
The first few chapters of John Terpsta's _Samba-3 By Example_ has the roadmap for this relatively simple case and just about anything else you want to use Samba for.
Some of the changes I made to my Samba configuration file are
[LIST=1]
[*]Include[INDENT]null passwords = yes[/INDENT]and[INDENT]security = share[/INDENT]in the global section
[*]Use the same workgroup name on both machines
[*]Added my local subnet to the "hosts allow" line
[*]Added entries for each share
[INDENT][sharename]
[INDENT]path = 
guest ok = yes
read only = no
[/INDENT][/INDENT]
[/LIST]
You have to restart samba to put changes into effect.
It also makes life easier to assign static non-routeable IPs to both your systems, and define them in each others' hosts-related files.
I'm taking it for granted that you're behind a firewall/router of some sort that's blocking ports 137-139 from your ISP, because you have to have them open on your machines to connect. And the world is crawling with slimeballs trying to break in on those ports.

---

### Post by cowlip on 2005-10-02
You can also try /etc/samba/smb.comf, change "encrypt passwords = true" to no.  Make sure you disable Zonealarm if yoiu have it.

I've also found that upgrading to breezy now lets me print to my windows shared printer from ubuntu

---

### Post by reidi on 2005-10-02
I finally got this working (Samba share set up on Breezy box and available from the network).  Even though I thought the default setup was to be authentication-less, I don't think that is the case.  No matter what I did, I always was prompted to authenticate whenever I connected to the server, and the authentication always failed.  
To get things to work,I had to explicitly set up a SMB user on the server box.

---

