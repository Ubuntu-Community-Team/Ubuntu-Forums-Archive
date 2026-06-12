---
title: "how to make the pound sign easy"
date: 2012-05-23
forum: Desktop Environments
---

### Post by a.m.wink on 2012-05-23
Hi - 

I have a US keyboard which produces a Euro sign (€) with the combination (Alt Gr)(5). When I try to implement the pound sign using xmodmap, it does not seem to work.

My current xmodmap setup is:
# xmodmap -pke | egrep 'dollar|Euro'
keycode  13 = 4 dollar 4 dollar
keycode  14 = 5 percent 5 percent EuroSign

So my thought was that the command 
# xmodmap -e 'keycode  13 = 4 dollar 4 dollar sterling'
would do the trick.

Except that it doesn't -- and the problem seems to be with the (4) key not xmodmap, because when I do
# xmodmap -e 'keycode 14 = 5 percent 5 percent sterling'
I can get the (5) key to produce a pound sign

Does that mean that the (5) key has a special status that the other keys don't have? Is there a command that makes it possible to let the (4) key work with (Alt Gr) as well?

Attached are my xmodmap settings (the output of xmodmap -pke). I understand some codes but not all of them!

Thanks,
AM

---

### Post by mister_p_1998 on 2012-05-23
Set UK region?

---

### Post by a.m.wink on 2012-05-23
Thanks, but that's not it (if I understand you correctly) - I don't have a UK keyboard.
Changing to the UK region does not change the layout of my keyboard. On UK keyboards the pound is above the (3), where the hash is on US keyboards.

Because the € sign is below the (5) and produced by pressing (Alt Gr), my plan was to define (Alt Gr)(4) as the pound sign.
For some reason though, the (5) is the only key that can be made to produce anything in combination with (AltGr)

What I mean is: if I show my keyboard mappings for 4 and 5 before changing anything
  >> # xmodmap -pke | egrep 'dollar|Euro'
  >> keycode  13 = 4 dollar 4 dollar 
  >> keycode  14 = 5 percent 5 percent EuroSign
it shows that the (4) key has no extra symbol 

But if I change both keys to show a pound sign
>> # xmodmap -e 'keycode  13 = 4 dollar 4 dollar sterling'
>> # xmodmap -e 'keycode  14 = 5 percent 5 percent sterling'
and show the keyboard mappings again
  >> # xmodmap -pke | egrep ' 13 =| 14 ='
  >> keycode  13 = 4 dollar 4 dollar
  >> keycode  14 = 5 percent 5 percent sterling
then the mapping for (5) has changed, but for (4) it hasn't.

Why is that???
(and can it be changed)

Thanks
AM

---

