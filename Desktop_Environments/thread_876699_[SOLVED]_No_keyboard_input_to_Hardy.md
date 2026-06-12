---
title: "[SOLVED] No keyboard input to Hardy"
date: 2008-08-01
forum: Desktop Environments
---

### Post by collier on 2008-08-01
Hi folks,  I need help!  My 3 month old installation of Hardy has just decided that it will not accept keyboard input at all.  I cannot use terminal, nor can I access root terminal.  I cannot edit my documents or images except by mouse controls.
Can anyone tell me what has happened?  And better still, can anyone tell me how to resolve the issue.

I am presently using the 'other' OS.  As you can see the keyboard works OK here.

Incidentally, I have been using Ubuntu for several years now.  I really like it.  Up to now I have had no problem with it apart from "operator problems", and I have been able to find a way to solve all of those with the help of these excellent forums.

BTW I suppose it might be obvious to some, but I should state it anyway.  I have keyboard input to the log-in screen, but not after that.  Obviously the problem is not in the kernel, but in Gnome.  Hence my decision to place this thread in the Desktop Environments forum.

Any clues . . .

---

### Post by mortenb on 2008-08-01
I had the exact same problem yesterday, when I somehow had managed to enable the "Slow keys" keyboard filter.

Go to System settings > Accessibility and then the "Keyboard filters" tab and disable "Slow keys" and you should be good to go :)



Btw. I am told that I probably enabled the "Slow keys" by holding down the Shift button for too long.

---

### Post by collier on 2008-08-01
> **mortenb said:**
> I had the exact same problem yesterday, when I somehow had managed to enable the "Slow keys" keyboard filter.

Go to System settings > Accessibility and then the "Keyboard filters" tab and disable "Slow keys" and you should be good to go :)



Btw. I am told that I probably enabled the "Slow keys" by holding down the Shift button for too long.


Thanks mortenb.  I checked this out as you suggested and found no solution.  Slow keys is disabled and I still have no keyboard input whatsoever.

Any other suggestions?  I have checked xorg,conf  -  it seems to be correct.  I have perused gdm.conf and can find no mention of keyboard there.

Is there some other controller of keyboard input of which I am unaware?

---

### Post by collier on 2008-08-02
This is getting really frustrating!:confused:  I still prefer to work in Ubuntu rather than this other OS  -  even with no keyboard input.  But every time I need keyboard I have to kill Ubuntu and start this other OS . . . Grrr!

I have carefully read the entire syslog contents to no avail.  I cannot see anything that looks suspicious.  I have worked through the entire Gnome desktop and found nothing that remotely suggests a switched off keyboard. I am unable to search the Help docs because I have no keyboard input.

I suppose I could reinstall Hardy, but that would be a pain and not tell me what is the problem in any case.  Besides, I have my /home folder on a separate partition so as to preserve my personal info and settings.  My guess is that whatever is causing this problem with no keyboard input is probably in my /home folder!  A clean installation would not resolve the problem in that case.

What can I do?

Can anybody help please?  :???:

---

### Post by collier on 2008-08-02
Wahoo!:)   All's well.   It appears that mortenb's suggestion was close to the money.

I eventually noticed that the default button under selected keyboard layouts section in System>Preferences>Keyboard was blank.  But I again disabled all of the Accessibility options as well, so I am none the wiser as to exactly which was the problem.  Whatever, I again have a keyboard.  I'd really like to know how this setting got changed in the first place . . .

---

### Post by collier on 2008-08-02
Just a note:  I feel like an idiot for not seeing the problem earlier.  However, this experience demonstrates the real value of these forums.  No matter how dumb the question, there is usually somebody who is prepared to help.  And further, there will probably always be someone else who will benefit from the discussion.

Thanks mortenb!  and all others who looked at this thread.

John.

---

### Post by manties on 2011-03-17
Thanks for posting this. Removing all the checks in the Aceessibility Panel under System>Preferences>Keyboard worked for me as well.

---

