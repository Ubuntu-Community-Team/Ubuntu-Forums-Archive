---
title: "Is it possible to set a default Network connection?"
date: 2014-09-18
forum: Desktop Environments
---

### Post by Robbyx on 2014-09-18
I have 3 profiles under the wired connect  network option. One is used virtually all the time but sometimes the other are loaded instead. How can I force one of the profiles to be the default?

Robin

---

### Post by tgalati4 on 2014-09-18
I don't know of a way to do it.  My impression is that [NetworkManager]("https://help.ubuntu.com/community/NetworkManager") uses a "sticky" network rule.  The last network that you connected to becomes the "default" network for future connections.  If that connection is not available then it will go to the next connection in your list of defined connections.  If no viable (and correctly-configured) network connections are available, it will wait until a device is plugged in (hotplug) or until you edit one of your connections with the correct settings.

Older network frameworks allowed you to drag a network connection to the top of the stack to give it "default" status.  If you needed to change the order of devices, you simply moved the one you wanted up to the top of the stack.  NetworkManager does not allow you to do that.

A little more searching:  [http://askubuntu.com/questions/321089/how-can-i-set-a-default-profile-for-a-network-interface-in-network-manager](http://askubuntu.com/questions/321089/how-can-i-set-a-default-profile-for-a-network-interface-in-network-manager)

The box "Connect automatically" in your connection editor will set it to the default.  Understand that you can have multiple connections with this setting, so it gets a little confusing if you have lots of networks and specific configurations for each.

---

### Post by Robbyx on 2014-09-19
The box "Connect automatically" in your connection editor will set it to the default. Understand that you can have multiple connections with this setting, so it gets a little confusing if you have lots of networks and specific configurations for each. 


I am hoping this was the solution. I have just disconected all the automatic connections except for the adsl connection and so  I should not have a random take up of connections when i start the system. 

R

---

### Post by tgalati4 on 2014-09-20
Let us know if it works the way you expect.

---

### Post by Robbyx on 2014-09-20
Yes. It works so that I only have one connection which will open automatically.

---

