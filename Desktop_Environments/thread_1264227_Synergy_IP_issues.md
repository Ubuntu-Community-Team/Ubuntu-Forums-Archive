---
title: "Synergy IP issues"
date: 2009-09-11
forum: Desktop Environments
---

### Post by redwards1987 on 2009-09-11
Hello everyone.

Somewhat new to Ubuntu, so before i begin i'm not very good with using the terminal.

My problem is with synergy. I have a vista pc running synergy as the server.  Ubuntu is the client (i found this to be the easiest way around synergy getting locked out of the admin messages in vista).  It works just fine. I even got it configured so that the synergy client (ubuntu) starts before i log in so i don't need a seperate keyboard on the ubuntu machine just to log in.  but now my problem is that every once in a while when the vista machine loads up and i log in, the ip address changes.  This doesn't happen often just once in a while.  in the past 3 weeks probably like 3 times. 

This wasn't really a problem before because when i'd start the client i would just start it with the new ip address in the terminal.  but now that i have it autostarting before log in and after log in through the start up applications using the ip address it's a pain.  everytime the ip address changes, i now have to modify the start up application and then go into my ..../Init/Default file and change the ip address in there.  

I've tried to connect synergy using the computer name which everyone says works but that hasn't worked at all, it can't find it (computer name is Windows).  it will only work with the ip address.  

Does anyone know how i can get the ubuntu machine to connect to the server using just the computer name. i've seen people modifying the .conf file for synergy to include aliases with the ip address but that still wouldn't work because it would still change, although i suppose i would only have to modify that one file when it did.  I suppose if anyone knows how to stop the ip address from changing on the vista pc that would be the better option.  thanks a lot in advance for any help.

Sorry for the post since i think i may have fixed it.  does this sound right to anyone? i went into the network properties and assigned an ip address to the computer instead of letting it select one.  sounds right to me and so far haven't had any problems.  Hope this works.

---

### Post by DouglasAWh on 2010-12-01
Did you change to a static IP on vista or on ubuntu?  You could set your machines to update DNS, but I'm struggling with that myself. Static IPs should certainly be doable.

I'm having trouble getting the server on Windows to accept screennames that start in numbers though, so I'm not entirely sure how that works.  I used to use IP addresses when ubuntu was the server.  I still do at home, but Windows doesn't seem to like it and I don't have another option on my corporate network, so it really sucks for now.

---

### Post by sarahfoxnz on 2011-04-02
Which IP addresses do you use ? 

I know about WINXP (ipconfig) / Ubuntu (ifconfig)..

But every few months - something causes the Synergy to stop (I don't use it often),  & IP addresses are the BIGGEST area I have in re-installing (or setting it up again..)

Which IP addresses do i use in ip/if config screens ?

(I did send a suggestion on the synergy forums..)

---

### Post by sarahfoxnz on 2011-04-07
Any ideas on how to extract / find IP addresses in the ipconfig/ifconfig screens ?

(what lines to look for etc...)

---

### Post by sarahfoxnz on 2011-04-07
what does Synergy (SERVER) show when a client has the correct IP address to connect - (but still I can't move to the client screen ?)

---

### Post by sarahfoxnz on 2011-04-07
Hmm..  The edit option on this forum ids showing, but its not allowing me to edit my posts.


I turned my client (ubuntu) / server (winxp) machines on - & my server machine went REALLY REALLY Slow  - & I can't switch to the other machine...


Slow = My curser commands were actioned a minute or two after I changed anything - Had to move real slow to turn synergy off...

---

### Post by Lozzy_uk on 2012-01-02
> **redwards1987 said:**
> ... I even got it configured so that the synergy client (ubuntu) starts before i log in so i don't need a seperate keyboard on the ubuntu machine just to log in...

Hi Redwards,

any chance you could let us know how you got the synergy client working before login??
I've been searching for the answer to this one for a while now.

thanks
Lozzy

---

