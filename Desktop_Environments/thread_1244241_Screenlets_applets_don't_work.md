---
title: "Screenlets applets don't work"
date: 2009-08-19
forum: Desktop Environments
---

### Post by Chogogo on 2009-08-19
Hello

I just installed Jaunty and I installed "Screenlets". I run the application and I come to the Screenlets Manager window, I Select an applets "for ex the clock" and then I click on "launch/Add" buttom but nothing happens! No applets comes up...not even an error message.

I have also gdesklets application and It works ok, but I like "screenlets"

What could be wrong? What can I do to fix it?

Thanks in advance for your help and may Gud bless you.

---

### Post by Razgriz PR on 2009-08-23
Sorry for not giving you and answer but I have the same problem and also trying to find a solution I was about to post a question when I found yours. Hope someone could help us.

---

### Post by hansdown on 2009-08-23
Hi Chogogo.

I'm using the basic clock as an example.

On the bottom left, check the "start/stop" box.

To make it run on login, check the "auto start on login" box.

---

### Post by Chogogo on 2009-08-23
> **Razgriz PR said:**
> Sorry for not giving you and answer but I have the same problem and also trying to find a solution I was about to post a question when I found yours. Hope someone could help us.
Hello. 
I Found a solution in another forum. It was a "permitions" problem.

Run the program from the terminal (open a terminal and write: screenlets  <ENTER>) then do the same(Try to activate a widget) 

An error message should come up in the terminal. I my case was a Lack of permisions to write a log file in certain folder. You can paste your output here to see whats going on.

The solution (in my case): Change the authorizations for this  folder (allow all user to write and read)   and It worked.

Hope this helps you.

Best regards and God bless you!

---

### Post by Razgriz PR on 2009-08-23
Hi, Thanks for the help, it looks like I forgot to change that folder's permissions hehe, Thanks alot!

---

