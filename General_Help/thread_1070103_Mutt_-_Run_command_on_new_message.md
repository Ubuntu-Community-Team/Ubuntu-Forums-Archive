---
title: "Mutt - Run command on new message"
date: 2009-02-14
forum: General Help
---

### Post by PhrankDaChickenGeek on 2009-02-14
Is is possible to run a shell script / command automatically when you receive an email message in Mutt? No keystrokes, nothing.

---

### Post by andrew.46 on 2009-02-16
Hi,

I would imagine that this could be done through procmail if you use this to process your mail. Can you be more specific about your mail setup and exactly what sort of script you mean?

Andrew

---

### Post by PhrankDaChickenGeek on 2009-02-17
I want to use gmail/imap.

I'm setting up a home automation system using SMS text messaging - I text the gmail address - my Ubuntu server gets the email, then executes a command based on the sender and body.

Right now I'm using a POP3, and just running Mutt so it'll download the mail and exit. Then I grep the mail spool for the body/sender and run commands accordingly. I have this set up in a script that loops every 3 seconds. This leads to problems - The script will sometimes die.

Cron can only be set to run once a minute, which is to long.

If I could just leave Mutt open in a Screen session....
I could make a macro - <save-message><esac-shell> do something <delete-message> - But that requires keyboard input....

---

### Post by andrew.46 on 2009-02-19
Hi,

Sorry but I have no idea how to go about that :(. Have you though of asking on comp.mail.mutt?

Andrew

---

