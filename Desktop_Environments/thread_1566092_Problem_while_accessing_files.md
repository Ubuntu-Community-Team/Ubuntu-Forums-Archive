---
title: "Problem while accessing files :/"
date: 2010-09-01
forum: Desktop Environments
---

### Post by generi on 2010-09-01
Hello all Ubuntuners :)

I am new in the linux enviroment and i am comfused with an issue that i have :)
I will try to be as clear as possible with the problem that i have.

There are 2 user accounts : 1)xio and 2)xio2

I was testing the new enviroment and i copied some precious files on xio2.
Unfortunately i could nt take back those files. the files are at home directory. I tried everything but i just cant copy-paste that files back to my hard disk where i have all my files.
I must say, that i deleted the user xio2.
But when i tried to create another xio2, i couldnt enter the enviroment.
the message was: 
"Could not update ICEauthority file /home/xio2/.ICEauthority.

I search over the forum but i couldnt find a solution.

If anyone can help my i will be grateful :)

Thanks again ):P):P

---

### Post by AlphaLexman on 2010-09-01
> **generi said:**
> i copied some precious files on xio2.
If it was just a copy do you still have the original?

---

### Post by generi on 2010-09-01
nope i moved them there.
The point was that i didnt want anyone to see them.;)

---

### Post by DonEsteban on 2010-09-02
You're probably posting in the wrong forum. From your description, I'm not entirely sure what you did, but it sounds like a problem with file permissions. You aren't allowed to access xio2's file while you're xio. You can do the following:
- Open a terminal (Applications--Accessories--Terminal)
- Enter "sudo nautilus" (this starts the file browser with super user (admin) privileges)
- It should ask you for your password and open the file browser afterwards
- Navigate to /home/xio2 and do what you want to do

**Be careful!** As a super user you can damage/delete every file on the system, so always think twice (or more) before you do anything!

You may want to delete xio2's home directory (i.e. /home/xio2), but again, be careful not to delete too much!

---

### Post by generi on 2010-09-02
Sorry for being off topic. :^o
As i said i am new in ubuntu and i am a little bit lost..
About sudo nautilus.
I did that and i have access to those files. The thing is that i can't copy them.
I can delete them, i can use them , but i can't make copies.
This is actually my problem :)
Thanks again :)

---

### Post by Old *ix Geek on 2010-09-02
> **generi said:**
> I tried everything but i just cant copy-paste that files **back to my hard disk** where i have all my files.Did you move them off your hard drive?
> The thing is that i can't copy them. I can delete them, i can use them , but i can't make copies.You're going to have to give us some more info! WHY can't you copy them? HOW are you trying to copy them? WHAT happens when you try? Are there error messages? What do they say?

It sounds like permissions issues, but without more info it's hard to help.

---

