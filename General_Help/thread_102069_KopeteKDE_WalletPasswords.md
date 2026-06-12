---
title: "Kopete/KDE Wallet/Passwords"
date: 2005-12-11
forum: General Help
---

### Post by WebDrake on 2005-12-11
Hello all,

After a few weeks of playing with the default GNOME setup in Ubuntu I decided to install kubuntu-desktop (and a few other goodies like Kdevelop), and it seems like a fun option. :-D

Anyway, I have one problem.  I set up Kopete with my ICQ, AIM, etc. accounts; but it uses KDE Wallet to store the passwords.  This wouldn't be, by itself, a problem: but at startup, it means having to enter the wallet password in order to log on to all the accounts in Kopete.  I'd rather not have to do that, I trust Kopete to log on straight away.

The second problem is that, if I *do* enter the password that allows Kopete to access the wallet, suddenly I can go into this same wallet and read all the passwords stored there ... !   Which is really, really not what I want.

So, how can I set things up to avoid these problems---to allow Kopete access to the passwords it needs, but without requiring me to enter data which potentially opens up those passwords to external scrutiny?

Many thanks,

          -- Joe

---

### Post by mlomker on 2005-12-11
[QUOTE=WebDrake]So, how can I set things up to avoid these problems---to allow Kopete access to the passwords it needs, but without requiring me to enter data which potentially opens up those passwords to external scrutiny?
[/QUOTE]

You could try removing the wallet altogether then it won't be able to use it, of course.  I don't really understand your concern about having the wallet be open when you're logged into your machine.  If you step away you should be using a password-protected screen saver.  I also use Firefox as my browser, so very few passwords are stored in there for me.

The reason that I said *try* to remove the wallet is because I've found that Kmail simply refuses to remember a password without the wallet installed.  It was prompting me for passwords all of the time and it irritated me a lot more than the wallet. I decided to leave it installed but remove the icon from the system tray.

```

sudo apt-get remove kwalletmanager

```

---

### Post by WebDrake on 2005-12-11
[QUOTE=mlomker]You could try removing the wallet altogether then it won't be able to use it, of course.  I don't really understand your concern about having the wallet be open when you're logged into your machine.  If you step away you should be using a password-protected screen saver.[/QUOTE]
Having the wallet open is not the *real* concern, to be honest.  The real issue is the pain in the arse necessity of typing the wallet password every time I log in to the system.  So I decided to risk not using the secure wallet at all for Kopete.

I use Thunderbird for mail so the Kmail issue isn't a worry. ;-)

Thanks for the advice!

---

### Post by daller on 2005-12-16
Where is the kopete-passwords stored, if not in the kwallet? (My sister forgot her password - And I need it for gaim now)

Any ideas?

---

### Post by jobezone on 2005-12-16
Can't kwallet be configured to close its wallet after a specified time?
On the other hand, this means you would have to retype it the next time an app needed a password from it.
I haven't used kwallet from a long time, but my brother has used KDE for over a year, and he uses it extensively. Also, it was handy for him to have kwallet for various reasons.
He got a new laptop, and installed kwallet in it. He opened kwalletmanager, and dragged his walled to a usb pen.
Then he put the usb pen in his laptop, and draged the kwallet to the laptop's kwalletmanager. Voil&#225;, he now has all his kde passwords in his laptop.

---

### Post by bobby555 on 2005-12-16
[QUOTE=jobezone]Can't kwallet be configured to close its wallet after a specified time?[/QUOTE]

Yes it can.

AM

---

### Post by mlomker on 2005-12-16
[QUOTE=WebDrake]The real issue is the pain in the arse necessity of typing the wallet password every time I log in to the system.  [/QUOTE]

lol.  My 'password' is hitting the spacebar once.

---

### Post by vh1 on 2005-12-16
can't you just create a wallet with no password specified?

I'm pretty sure that works. the dialog comes up, but you just have to hit return

---

### Post by supenguin on 2005-12-16
You can configure your wallet with no password so you won't have to type your password in every time. You can also configure kwallet to not show up on the system tray.  Not sure if that helps you or not, but that's the way I have my system set up.

---

### Post by mlomker on 2005-12-16
[QUOTE=supenguin]You can configure your wallet with no password so you won't have to type your password in every time. [/QUOTE]

I couldn't get it to do that.  Hiding the icon is easy.

---

### Post by joey111 on 2006-04-01
i always get asked for my pop passwords in kmail , how could i get them stored in the kwallet? ( maybe I declined that option in the beginning, how coul i reactivate that?)

---

### Post by exodus on 2006-04-02
hi m8..

u could do wat i did.. like u said its a pain really to keep typin de password everytime...

so i used synaptic to install the kde wallet in ubuntu..

then i ran wallet manager from system... there i disabled kde wallet.. now i dont have to type in de passord everytime.. kopete works fine..

---

### Post by joey111 on 2006-04-03
well if i wouldnt need  to enter it once ( my overall password for the wallet) it would be ok, but kmail doesnt store the pop passwords there what i would prefer. So unfortunately i would need to enter 3 pop passwords; i just want to get them stored but how!

---

### Post by yugo on 2006-09-21
It seems there is some problems beetween kmail/kontact and kwalletmanager (it's wierd, kmail store the passwords but kontact try to access them). Now I no more use kwallet to store my kmail passwords. I deleted my kmail account in kwallet, and prevent kontact from accessing kwallet.
Now kmail stores my password by itself. It's less safe but at least it works.

edit: it no more works! I don't really know how I made it worked...

---

