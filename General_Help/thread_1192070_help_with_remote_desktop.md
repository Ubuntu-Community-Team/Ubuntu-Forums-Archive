---
title: "help with remote desktop"
date: 2009-06-19
forum: General Help
---

### Post by philcamlin on 2009-06-19
hi i have remote desktop setup on my server (9.04 with gui) so i dont have to use a screen . logical enough... because its in my furnace room

how can i make a remote desktop go to external ip cause when i go to it it says its only reachable over the local area network. is there any way i can make it so i can vnc into it from minniapolis or something ?

i know my ip and ive tried port forwarding but it doesnt work :mad:

PLEASE HELP 

i have files on there and i need access to them where ever:popcorn: and its not Pr0n if thats what your thinking

---

### Post by philcamlin on 2009-06-19
bump

---

### Post by rampageoberon on 2009-06-19
Under the Preferences -> Remote desktop -> Advanced tab, make sure "Allow local connections only" is not ticked.

You then need to make sure that the portforwarding has been done correctly.

You can use utorrent's portchecking tool for this for example [http://www.utorrent.com/testport.php?port=5900](http://www.utorrent.com/testport.php?port=5900) if you have left the remote desktop port to default.

Hope that helps

---

### Post by philcamlin on 2009-06-20
where do i find this advances tab theres nothing there :P

just remote desktop window :mad:

please help :)

[[IMG]http://img197.imageshack.us/img197/2244/screenshotibn.th.png[/IMG]](http://img197.imageshack.us/i/screenshotibn.png/)

---

### Post by philcamlin on 2009-06-20
sorry but my plane leaves for minni in like an hour so i need an answer quick thanks guys! :popcorn:

---

### Post by philcamlin on 2009-06-20
aha i got it thanks :popcorn:

---

### Post by iammatthew2 on 2009-07-28
> **philcamlin said:**
> aha i got it thanks :popcorn:
 I'm in the same situation. 
 
How did you solve it? Where is the "advanced tab"?

---

### Post by XCan on 2009-07-28
> **iammatthew2 said:**
> I'm in the same situation. 
 
How did you solve it? Where is the "advanced tab"?

They removed the "advanced" tab, but you can find all the previous options in gconf-editor (type in terminal) -> desktop -> gnome -> remote_access.

---

### Post by rbc on 2009-07-28
I have been wondering about this also, although I have not figured out how to port forward my router, but I looked in gconf-editor-> desktop -> gnome -> remote_access. I have the "enabled" option checked. The "local only" option is unchecked. What am I missing?

---

### Post by XCan on 2009-07-29
If you want to port forward on your router you'll have to refer to its manual or [http://portforward.com/](http://portforward.com/) for a guide.

---

