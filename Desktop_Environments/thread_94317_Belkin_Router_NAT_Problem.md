---
title: "Belkin Router NAT Problem?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by InsomniacUK on 2005-11-23
Hey everyone,

Been using Ubuntu for a while now, and love it, but I am having some networking problems. I like to consider myself rather computer literate, but I am not used to using a router to access the internet, I used to use a USB modem on Windows.

I am now using a Belkin wireless router to share my ADSL connection between my Ubuntu box and my parents XP box downstairs. It has a built-in firewall.

Now, my problem is centred around Azureus. In order for decentralised tracking to work, it requires port 6881 TCP/UDP to be open. Now, to the best of my knowledge, I have set the firewall router to allow traffic inbound and outbound of port 6881, but still, whenever I test Azureus, it returns "NAT Error".

I'm really stuck for ideas now, but from the limited knowledge I do have of networking, a NAT error would presumably relate to the router itself?

Can anyone please give me some advice on how to get Azureus fully functional?

**Edit:** Sorry, I wasn't sure whether this is a hardware or software issue, if it's more likely to be a hardware issue, could a mod move it please?

---

### Post by C@t-M@n on 2005-11-23
make sure that the router is configured to forward requests on port 6881 to your machine's ip and that port 6881 is open on the ubuntu box if you are running a firewall on it.

---

