---
title: "want to ubuntu through bash commands sent by email"
date: 2008-12-08
forum: General Help
---

### Post by das867 on 2008-12-08
I would like to control my ubuntu 8.04 installation via bash commands sent by email, simple things like print and shutdown, but i'm not sure how to go about it. i would like to use evolution for this, and i've already searched google and found nothing like a perfect fit. it would be awesome if it were flexable,as in all bash commands, and it doesn't have to send back terminal output back. any help would be awesome, and yes it pretty much has to be email, i don't want to to have to sign on IM and talk to a bot, not that theres anything wrong with that, i just don't like using IM. Any sugestions would be awesome. 

thanks.

/Das867

---

### Post by Het Irv on 2008-12-08
Why not SSH or any of the other technologies designed to do this.  If the answers is just because... or to get around filtering, thats fine, just curious.

---

### Post by das867 on 2008-12-08
> **Het Irv said:**
> Why not SSH or any of the other technologies designed to do this.  If the answers is just because... or to get around filtering, thats fine, just curious.

It's just because i'm frequently away from my computer, and sometimes ssh or telnet or other solutions are just not an option, wether because i'm on a public computer, or i dont have my flash drive, or some other reason. And for the fact that its usually more convientent. Also, if this works, it would be nice to be able to just send an email from my phone to control my computer.

---

### Post by Dr Small on 2008-12-08
Sending commands via email would not be very secure, because there is no authentication; Meaning, anyone could spoof the from address, and tell your system what to do.

Het Irv's suggestion is a better solution.

---

### Post by das867 on 2008-12-08
> **Dr Small said:**
> Sending commands via email would not be very secure, because there is no authentication; Meaning, anyone could spoof the from address, and tell your system what to do.

Het Irv's suggestion is a better solution.

ya email would be insecure, but i'm sure i could take any anwser that i get here, and have it only respond to email from a certain sender, or subject line, i'm just at a loss to set up the initial system.

---

### Post by das867 on 2008-12-09
at this point i've just settled for evolution activating scripts in response to certain subject line+sender+body of message. thanks for your help though

---

### Post by karlr42 on 2008-12-09
Well then be very careful with who you give that email address to. ssh is a much better solution.

---

### Post by das867 on 2008-12-09
> **karlr42 said:**
> Well then be very careful with who you give that email address to. ssh is a much better solution.

as much as I'm aware of that, i give my email address password to know one, and its not tied to receiver, its tied to sender.

---

### Post by karlr42 on 2008-12-09
If you use it to register on any site(like this one) there's a chance they could be compromised by crackers, and they would have your address.

---

### Post by das867 on 2008-12-09
yes but it responds to a thirteen digit codefrom a email address that i did not register to this site with (or any other site for that matter). in fact i just created the email address for this specific reason. so it would be harder then you think.

---

### Post by guX on 2008-12-09
If it's possible to run a web-server on that box, you might want to try something like ajaxterm. (apt-get install ajaxterm)

---

### Post by das867 on 2008-12-09
> **guX said:**
> If it's possible to run a web-server on that box, you might want to try something like ajaxterm. (apt-get install ajaxterm)

who said anything about web server?

---

### Post by guX on 2008-12-09
I did. Ajaxterm is basically a web-based SSH client. You run it from a webserver on your box, which you can then connect to remotely.

See: [http://wiki.kartbuilding.net/index.php/Ajaxterm](http://wiki.kartbuilding.net/index.php/Ajaxterm)

---

