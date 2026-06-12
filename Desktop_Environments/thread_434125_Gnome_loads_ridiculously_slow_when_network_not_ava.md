---
title: "Gnome loads ridiculously slow when network not available"
date: 2007-05-05
forum: Desktop Environments
---

### Post by fearpi on 2007-05-05
Whenever my wireless card is configured for an area I am no longer in, and I start up my computer, Gnome loads very, very slowly. The computer boots just fine, but when I log in, the gnome panels are blank, the wallpaper takes forever to load, the Beryl window decorator doesn't load sometimes. This happens regularly. I have disabled all network-related programs in Preferences->Session. How can I fix this?

---

### Post by woodgdo1 on 2007-05-05
Sometimes this can be caused by not resolving your own hostname in DNS. From a terminal, execute the following two commands and paste the output. 

hostname

cat /etc/hosts

---

### Post by fearpi on 2007-05-06
Output of "hostname" is "virgon".

Output of "cat /etc/hosts" is nothing significant - just three commented lines.

---

### Post by woodgdo1 on 2007-05-07
If the lines are commented out, that is probably bad. Usually it is in a form like this. (at least on feisty) 

127.0.0.1       localhost
127.0.1.1       myhostname.mydomain.net    myhostname

Another more normal Linux form would be:

127.0.0.1       myhostname.mydomain.net     myhostname      localhost       localhost.localdomain           

Your hosts file is used to bypass DNS resolving and is useful for instances when DNS servers are unavailable, such as when not connected to a network. Gnome usually needs to know the IP address of your hostname and localhost in order to do some of its functions. The 127.x.x.x class of addresses always point back to the loopback address on your system, which is always up even when not connected to the network.

myhostname  in the example above should be virgon on your system. The mydomain.net is not required unless you are within a Business internal domain.

---

### Post by fearpi on 2007-05-07
Great, thanks! That did the trick. Any reason that my list would have been empty?

---

