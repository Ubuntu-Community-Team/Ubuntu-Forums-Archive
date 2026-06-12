---
title: "apt-get update not working (8.10)"
date: 2008-12-10
forum: General Help
---

### Post by lviggiani on 2008-12-10
Hi,
I have a problem:
when I start either Synaptics or update manager or even sudo apt-get update
the system is not able to perform this action. For each repository I get the following error:
```
Could not resolve 'xxx'
```
where xxx is 'archive.canonical.com' and any other repo I have in my sources.list
The funny think is that my internet connection is working fine, I can use the web, mail, skype, amule etc.
The other funny thing is that if I run
```
ping archive.canonical.com
```
or any other repo, it resolves the name and the ping responds.
I'm connected via wireless.
Any idea?
Thanks in advance!

---

### Post by oldos2er on 2008-12-10
Go to System, Administration, Software Sources, and try different servers.

---

### Post by taurus on 2008-12-10
Did you happen by any chance install anon-proxy or something similar to that?

---

### Post by lviggiani on 2008-12-10
> **oldos2er said:**
> Go to System, Administration, Software Sources, and try different servers.

Already tried... same result.

---

### Post by lviggiani on 2008-12-10
> **taurus said:**
> Did you happen by any chance install anon-proxy or something similar to that?
I'm not sure I understand what you mean... :(

---

### Post by lviggiani on 2008-12-10
The last think I installed is
vodafone-mobile-connect-card-driver-for-linux
for my vodafone internet key 8and then I discovered that It was already supported by network manager).
Among the dependencies there is
linux-headers-2.6.27-7
where as my kernel is 2.6.27-10-generic

---

### Post by Coreigh on 2008-12-10
Does Apt-get return the error/failure for *ALL* sources, or just some?

You internet is working (you can see web pages) so have you tried going to the sources through firefox to make sure that the repo is actually working?

I just went to [http://archive.canonical.com/](http://archive.canonical.com/) with FireFox and it does work.

---

### Post by lviggiani on 2008-12-10
> **Coreigh said:**
> Does Apt-get return the error/failure for *ALL* sources, or just some?

You internet is working (you can see web pages) so have you tried going to the sources through firefox to make sure that the repo is actually working?

I just went to [http://archive.canonical.com/](http://archive.canonical.com/) with FireFox and it does work.

None of repo is working!!!
The funny thing is that if I do sudo apt-get install *"something"* it downloads and installs! However I get a warning that the package cannot be authenticated.

---

### Post by taurus on 2008-12-10
Why don't you post your /etc/apt/sources.list then?

```
cat /etc/apt/sources.list
```

---

### Post by frankleeee on 2008-12-10
> **lviggiani said:**
> None of repo is working!!!
The funny thing is that if I do sudo apt-get install *"something"* it downloads and installs! However I get a warning that the package cannot be authenticated.

Some packages have the authentication warning if it is a third party download. Post you apt source list and let the people who can look it over check for any errors that might be causing problems.

---

### Post by m0nty75 on 2008-12-10
has the actual path to the repository changed?

i have just had this issue when i came home from work and had the exclamation prompt alerting me to an issue, and the address to the repos wasn't valid anymore

although i'm using archive.ubuntu.com

it was ok this morning..

but i just had to go in and change the path.

it looks like the path has changed for canononical too >

previous > [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

now > [http://archive.canonical.com/dists/ubuntu](http://archive.canonical.com/dists/ubuntu)

seems they have been moved to a new directory called dists.

---

### Post by frankleeee on 2008-12-10
> **m0nty75 said:**
> has the actual path to the repository changed?

i have just had this issue when i came home from work and had the exclamation prompt alerting me to an issue, and the address to the repos wasn't valid anymore

although i'm using archive.ubuntu.com

it was ok this morning..

but i just had to go in and change the path.

it looks like the path has changed for canononical too >

previous > [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

now > [http://archive.canonical.com/dists/ubuntu](http://archive.canonical.com/dists/ubuntu)


seems they have been moved to a new directory called dists.

What server are you using, I use the main server and have not had this change show in the last few minutes upon doing a update check, and the dist url is a 404 error.

---

### Post by m0nty75 on 2008-12-10
well as i said, i use the ubuntu archive not canonical.

but in my case i've had to change from >

deb [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy main universe
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy main

to

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main


but in my list i had for canonical >

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

but if i visit [http://archive.canonical.com](http://archive.canonical.com)

i see no ubuntu directory, only a dists, pool & projects.. ubuntu has been moved into dists directory.

---

### Post by m0nty75 on 2008-12-10
sorry double postsed.. please delete this post. thanks.

---

### Post by lviggiani on 2008-12-11
I tried twice 5 minutes ago, from my work place (with original repos) and all worked fine.
I tried again 2 mins ago and it succeeded but it took around one minute to connect to archive.canonical.com...
I'll try again this evening from home to see what happen.

---

### Post by decoherence on 2008-12-11
EDIT #2: Figured it out! Rather than setting http_proxy I went to System > Preference > Network Proxy, set the proxy information there, told it to apply system wide and now it works!

Here's the rest of my post for post-erity (nyuk nyuk)

-----------------

I have also been having this problem for the last few days. I've tried different mirrors and in each case I'm able to browse the mirror with a web browser but apt-get update never gets past 

0% [Connecting to archive.ubuntu.com (91.189.88.40)]

And whatever other repos it's querying. I think the problem is definitely not the repos as the behavior is the same regardless of which repo I use and, as I mentioned, I can browse them with firefox.

I have tried with and without $http_proxy set (10.9.1.1:8080) and I have checked the packet filter's logs and see no evidence of it messing with this connection. Furthermore, I'm using http repos -- as I understand it, if the firewall lets me browse the web, it should let me apt-get. Am I wrong?

I'm a fairly experienced user so this is a real puzzle to me.

ADD: I am able to update from other machines so definitely not a firewall thing

sources.list

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20081001)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

kernel is 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64

---

### Post by lviggiani on 2008-12-11
Hi, still no luck from home... :(
Today it was working from my work place but is not working now from home...

Same problem as yesterday with the funny thing that I can ping archive.canonical.com and it responds and I can also browse it with firefox.

Attached are the terminal output on "sudo apt-get update" and my sources list.
Thanks for your help!

---

### Post by lviggiani on 2008-12-13
> **lviggiani said:**
> Hi, still no luck from home... :(
Today it was working from my work place but is not working now from home...

Same problem as yesterday with the funny thing that I can ping archive.canonical.com and it responds and I can also browse it with firefox.

Attached are the terminal output on "sudo apt-get update" and my sources list.
Thanks for your help!

Another interesting think is that from a virtual machine (Ibex) having as a host my computer (the one that does not atp-get update) the virtual machine does!
I'm about to re install ubuntu if no other suggestion will come...
Please help!!!

---

### Post by lviggiani on 2009-01-15
I solved my problem by replacing the sources.list file with one from a fresh installation of Intrepid and then adding again my third party repos.

---

