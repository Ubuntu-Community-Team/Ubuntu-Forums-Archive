---
title: "Somethings wrong with my ubuntu jackalope"
date: 2009-06-19
forum: General Help
---

### Post by superpink99 on 2009-06-19
ok lately my ubuntu was freaking me out, some of my applications just disappeared, for example my limewire it just disappeared(i did not uninstall it. when i go to senaptics to install it again, its gone!!! Now my pidgin is not working also, now when i update it says that my repositories does not have valid ID or something.

when i reload my synaptics it says: NO PUBLIC KEY


need help please...........:sad::sad::sad:

---

### Post by kostkon on 2009-06-19
> **superpink99 said:**
> ok lately my ubuntu was freaking me out, some of my applications just disappeared, for example my limewire it just disappeared(i did not uninstall it. when i go to senaptics to install it again, its gone!!!
OK, OK. First of all, try searching for Limewire in Synaptic using the full search, not the quick-search. I am pretty sure you will find it. You can mark it for reinstallation or you could even visit its website to see if there is a new version of it to install.
> **superpink99 said:**
> Now my pidgin is not working also, now when i update it says that my repositories does not have valid ID or something.
What problems exactly do you have with Pidgin?
> **superpink99 said:**
> when i reload my synaptics it says: NO PUBLIC KEY
Could you open a terminal and give
```
sudo apt-get update
```
and post the output here? It will ask for a password, give yours.

---

### Post by superpink99 on 2009-06-19
when i use terminal to update it still says some of the updates were ignored. can someone give me good third party repos:

and this is what appears when i reload my synaptics:

W: GPG error: [http://apt.wxwidgets.org](http://apt.wxwidgets.org) jaunty-wx Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E0BCE7F53B087BC
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5115B98AA836CA8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

---

### Post by kostkon on 2009-06-19
> **superpink99 said:**
> when i use terminal to update it still says some of the updates were ignored. can someone give me good third party repos:

and this is what appears when i reload my synaptics:

W: GPG error: [http://apt.wxwidgets.org](http://apt.wxwidgets.org) jaunty-wx Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E0BCE7F53B087BC
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5115B98AA836CA8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
OK, to add the key for the wxwidgets repository, open a terminal and give this:
```
curl http://apt.wxwidgets.org/key.asc | sudo apt-key add -
```

To add the keys for the two PPAs that you have, do
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B5115B98AA836CA8
```
and
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9423A34CCA967634
```
and then give a
[HTML]sudo apt-get update[/HTML]
and you should be fine.

---

### Post by superpink99 on 2009-06-19
ok first of all thanks Kostkon, what you just sent me solved the problem of updating, but what i wanna know is how in heaven do you know this things and i don't? that's not fair i should know also this things so will not always depend on smart people like you. hehehhee

mind telling me where you learned it........

ok new problem just arrived: when i install skype using synaptics this pops out:

skype:

Package skype has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

wors its the same with other applications

---

