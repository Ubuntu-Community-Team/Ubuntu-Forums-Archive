---
title: "Enterprise Desktop"
date: 2009-03-05
forum: General Help
---

### Post by Darryl Moore on 2009-03-05
Hi all.

There should be a support category for Enterprise Installation/Maintenance issues. I'm thinking this will become a bigger and bigger topic of conversation in the future.

I am currently trying to figure out how close Ubuntu (or any free linux distro) is to being ready to take a place on the corporate workstation desktop. I have seen a few posts in places where it has been done, but generally only with SLED or Xandros which are not free. Ubuntu could do it.

There are a number of free or cheap groupware options for a linux world which are still compatible with windows. Though I am still trying to figure out which are the best ones for any particular organization.

Having OpenOffice 3.0 with OOXML support, and now with MSOFFICE 2007 SP2 support for ODF, the strangle hold MS has over office software is loosening. 

It is fairly straight forward to make custom distributions CD images for individual organizations via [this thread]("http://ubuntuforums.org/showthread.php?t=688872&highlight=custom+iso")

Two things are needed before Ubuntu can do well here.
1) An easy GUI way to install and configure LDAP on both server and client machines.
2) An easy central mechanism to coordinate and administer updates to all network machines.

I have found no easy way to do either of these things, which is too bad. I know a couple small companies which currently have a few Linux machines, but their infrastructure is still predominantly Windows. If these problems could be addressed, then it would be pretty easy to convince them to switch, which I'd like to do.

---

### Post by ju2wheels on 2009-03-05
Honestly, besides providing official support for the server version of Ubuntu, its main goal/focus has been on the desktop. However, it appears this is going to change with the release of Karmic Koala Ubuntu 9.10 in October later this year. It will supposedly look to provide a solution to running Ubuntu on servers, or more specifically in VM's in a cloud. However I think the similarities would make your suggestions useful for both implementations (either in a cloud or as distinct installations across servers).

I would thus recommend you create posts on ubuntu brainstorm to gather support for these features being developed during the Karmic Koala development time frame (April - October).

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)

---

### Post by Darryl Moore on 2009-03-05
I agree completely. But so far as I have seen the desktop solutions that Ubuntu (and most other distros) offer are pretty much limited to single (i.e. home use) installations.

Without a way of managing updates and simplifing LDAP for both client and server, it will be very hard to make inroads in the corporate world. 


A corporate Ubuntu desktop distro with built in LDAP authentication, groupware and some client to manage centralized updates together with a corporate groupware server distro would be awesome. That is in fact what I would like to try to put together so that I can offer it to many of the small businesses in my community.

---

### Post by ju2wheels on 2009-03-05
One of your problems has a relatively simple solution.

In terms of managing updates on across clients and servers, you can create a centralized update server on your network whose sole purpose is to distribute upates to your cleints and servers. 

Then you can customize your client server images such that the software sources(repositories) used point to your internal server instead of the standard ubuntu repo servers and enable automatic install of updates from the internal repo. 

In this manner you control which updates get distributed and control whether or not you want to pass on Ubuntu's updates to your clients/servers. This is actually how they did it at my job with Redhat.

---

### Post by Darryl Moore on 2009-03-05
Yes, thx. That is an excellent idea, though it still does not give me the level of control I would have in an MS network. 

What about LDAP? I think you want to make setting up a network wide enterprise installation to be almost as staight forward and easy as doing so with Windows. Currently it is anything but. An out-of-the-box sollution here would benefit many people.

---

