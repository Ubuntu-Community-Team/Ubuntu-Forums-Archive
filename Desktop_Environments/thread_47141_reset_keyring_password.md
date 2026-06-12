---
title: "reset keyring password?"
date: 2005-07-07
forum: Desktop Environments
---

### Post by roots on 2005-07-07
hi....

i already posted this at ../security/ but meanwhile it seems a bit OT to me there...
so here we go...

something really silly happened just a few minutes ago: i tried to connect to some smb shares on a remote pc, i was asked for the smb password and if i want to store it in the keyring file. i decided to do so, then i was asked to set a keyring password.
then it happened...i started typing the password, made a typo but at the same time i accidentally hit the touchpad and "managed" to confirm this incomplete and wrong password. very funny i thought, and up to now i tried quite a few combinations to find the "wrong password" but without success.

can anyone tell me where/how to set or reset the keyring password? i got root access so this shouldn't be the trouble...
um by the way...i'm using ubuntu 5.04.

thanks in advance!
.roots

---

### Post by hippyjim on 2005-09-05
Has anyone come up with an answer for this? I'm facing a similar situation where the default keyring is locked, and I don't know where I even **set** the password!

---

### Post by hippyjim on 2005-09-07
Ok facing the usual lack of help in this forum, I had a fiddle myself. I opened Nautilus as root, and found ~/.gnome2/keyring and deleted the file called "default".

I then created a new keyring with the gnome-keyring-manager, and made it the default. I set a password (not the same as my login password) during the creation process.

I logged out, and back in, just to see if that had fixed the problem.

I was asked for the usual blinding array of passwords, including for the new default keyring. I entered the password I created, and the rompt for the password came back again. I did this roughly 30 times (to make sure it wasn't just a whole load of requests made by my having to try so many different things with the keyring previously).

I eventualy tried my gnome login password - and hey presto! I was then given the option to "always" allow the nome-panel, and nautilus to access the default keyring.

All was good - using a password I hadn't chosen. Unfortunatly I now get asked that password twice every time I log in, then I get asked if it's okay to allow access - but at least I know what to enter!

I'm really beginning to think that "community supported" software is a waste of time - especially with a community that's so full of its "humanity to others" moral that it forgets how to be human. I hope my experience helps someone - nobody has ever helped me on this forum.

---

### Post by codejunkie on 2005-09-08
[QUOTE=hippyjim]Ok facing the usual lack of help in this forum, I had a fiddle myself. I opened Nautilus as root, and found ~/.gnome2/keyring and deleted the file called "default".

I then created a new keyring with the gnome-keyring-manager, and made it the default. I set a password (not the same as my login password) during the creation process.

I logged out, and back in, just to see if that had fixed the problem.

I was asked for the usual blinding array of passwords, including for the new default keyring. I entered the password I created, and the rompt for the password came back again. I did this roughly 30 times (to make sure it wasn't just a whole load of requests made by my having to try so many different things with the keyring previously).

I eventualy tried my gnome login password - and hey presto! I was then given the option to "always" allow the nome-panel, and nautilus to access the default keyring.

All was good - using a password I hadn't chosen. Unfortunatly I now get asked that password twice every time I log in, then I get asked if it's okay to allow access - but at least I know what to enter!

I'm really beginning to think that "community supported" software is a waste of time - especially with a community that's so full of its "humanity to others" moral that it forgets how to be human. I hope my experience helps someone - nobody has ever helped me on this forum.[/QUOTE]

just had the same problem myself delete the $HOME/.gnome2/[COLOR=Red]keyrings[/COLOR] folder then you can enter a new password when you get prompted by the gnome keyring daemon hope this helps.

---

### Post by psypher on 2005-09-12
> I'm really beginning to think that "community supported" software is a waste of time - especially with a community that's so full of its "humanity to others" moral that it forgets how to be human. I hope my experience helps someone - nobody has ever helped me on this forum.

I'm sorry to hear that. I could go on and on about why, but who cares. I have gotten quite a bit of help from these forums and from the mammoth amount of posts about almost every bug I have encountered I think the help is definitely out there.

post on here which threads you have posted and i'll do my best to help you out. 

after all, this one just helped me. thanks

plus if HP is willing to sell hardware with ubuntu on, then something must be going right!

---

