---
title: "Ubuntu installed on a school computer lab - need to block web pages"
date: 2009-03-30
forum: General Help
---

### Post by jamieh on 2009-03-30
Hi,

I have installed Ubuntu on a small private school's computer lab. It consists of 12 computers and a server.

Since it's a school, I'm required to block the standard. Porn, games, facebook, etc.

Is there a program that can do this? I want it to show a "friendly" block screen instead of just saying "Unable to connect", and I'd like it if one configuration would effect the entire network.

Thanks

---

### Post by kanikilu on 2009-03-30
There's other information out there, but here's a pretty thorough guide on how to do this. It's not trivial, though...

[http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php](http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php)

---

### Post by iaculallad on 2009-03-30
> **jamieh said:**
> Hi,

I have installed Ubuntu on a small private school's computer lab. It consists of 12 computers and a server.

Since it's a school, I'm required to block the standard. Porn, games, facebook, etc.

Is there a program that can do this? I want it to show a "friendly" block screen instead of just saying "Unable to connect", and I'd like it if one configuration would effect the entire network.

Thanks

Had you tried thinking of using a dedicated machine to do that tedious task for you? Does IPCop/Smoothwall/PFSense ring a bell?

---

### Post by ibuclaw on 2009-03-30
Easiest way to do that would be to use the hosts file that your school server uses, and redirect all blocked site to yourself.

ie:
```
sudo gedit /etc/hosts
```
And put inside:
```
127.0.0.1 www.google.com
```
Save and Quit, now try and access google... you can't

What does this have to do with a user-friendly page?
Well, install apache2
```
sudo apt-get install apache2
```
then
```
sudo gedit /var/www/index.html
```
And use your html scripting skills (or, admittedly, you **can** create one in OpenOffice) to make a site page.

Here is my random example:
```
<html><body><h1>Site Blocked!</h1></body><img src="http://farm4.static.flickr.com/3268/2448556992_fb586ee441.jpg" alt="Site Blocked" /></html>
```
Save, quit, and reload the page, and you should see what you've made.

Now ... as for making a configuration to take effect on **the entire network** ...
Presume that the entire school goes through a proxy. Setup the exact same thing as above, but on the proxy server.

Regards
Iain

---

### Post by aysiu on 2009-03-30
OpenDNS may be able to help you manage filtering.

---

### Post by asmoore82 on 2009-03-30
> **jamieh said:**
> Hi,

I have installed Ubuntu on a small private school's computer lab. It consists of 12 computers and a server.

Since it's a school, I'm required to block the standard. Porn, games, facebook, etc.

Is there a program that can do this? I want it to show a "friendly" block screen instead of just saying "Unable to connect", and I'd like it if one configuration would effect the entire network.

Thanks

the school should already have a network-wide solution in place -
some sort of gateway monitor or transparent proxy.

---

### Post by kanikilu on 2009-03-30
> **asmoore82 said:**
> the school should already have a network-wide solution in place -
some sort of gateway monitor or transparent proxy. That's a bit of an assumption, isn't it? Besides, even if the school does, it's always possible that he wants to have further control over a subset of computers (in this case, a lab), rather than accepting the default inherited down by the network-at-large...

---

### Post by jamieh on 2009-03-30
Thanks, I'll try Tinivole's solution.
I just hope the tech-savvy kids won't get past this. The student account is a "Desktop user".

---

### Post by ibuclaw on 2009-03-31
1) Attempt to do this:
```
sudo -s
```
While in the student account. If it denies you after you use the student password, then they won't be able to gain the permissions to change the file. Unless they know **Y0ur_Pa$$w0rd** and use **su jamieh** (or whatever your account name is) to gain access to your account.

2) I presume that your school keeps a list of all sites that they block?
If so, that should make the job easier.

Else, bodhi.zazen hosts a generic adblock script that should give you a good base list to start from: [http://bodhizazen.net/adblock/adblock-0.98.sh](http://bodhizazen.net/adblock/adblock-0.98.sh)

Regards
Iain

---

### Post by srdjo on 2009-09-20
TNX tinivole, worked great

---

### Post by sideaway on 2009-09-20
Block external proxies. We used to run rampant on those things when I attended school :P

---

