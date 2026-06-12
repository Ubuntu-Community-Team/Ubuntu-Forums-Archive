---
title: "Cant log into Ubuntu. what do i do"
date: 2009-04-09
forum: General Help
---

### Post by robinbj on 2009-04-09
I have loaded Ubuntu using Wubi and when prompted, entered in my username and password. That doesnt work now for the actual log in screen. What should I do

Bradley Robinson

---

### Post by PreviousN on 2009-04-09
There is no reason why what you entered when installing via wubi wouldn't work. I know it sounds silly and maybe a little demeaning, but EVERYTHING in linux is case sensitive, including passwords. If you entered your password with caps lock on, then you'll have to enter your password in caps. So, before resorting to the below options, make sure that you are typing the password in the same way, and in the same capitalization that you installed it with. After that, you have a few options: 

Option 1. Go back into windows and try reinstalling ubuntu via wubi. Then, be more careful with entering a password. Ubuntu, like windows, doesn't just change a user's password of its own accord. Chances are you accidently made a typo originally or accidently hit the shift key. 

Option 2. If you are using GRUB- the linux bootloader, (I think wubi installs grub), you should be able to (when you first boot your computer) choose a system recovery mode of ubuntu. This will get you to a menu (if I recall correctly). Choose to go to a terminal. A terminal is a command prompt that looks like this: 

previousn@raptop:~$ 

Essentially it is your username (which for you would read "root"), an @ sign, referring to the name of your computer. And then the prompt. At this prompt, enter this:

passwd <your username> 

And then it will prompt you to enter a new password. 

So, anyways, I think in your case the easiest solution, assuming that you are new to linux, would be to reinstall and be more careful when you enter a password. It happens to the best of us. I used to work as a help desk consultant, and a coworker of mine accidently when resetting an administrative password entered it wrong, even when asked to confirm (same typo both times). He had to go through some major steps to get the computer back since he couldn't get the password right after that!

---

### Post by robinbj on 2009-04-09
Thanks. I appreciate that.

---

