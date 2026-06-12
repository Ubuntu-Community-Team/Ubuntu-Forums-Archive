---
title: "Login screen fail"
date: 2011-09-22
forum: Desktop Environments
---

### Post by Faziri on 2011-09-22
Hiya all

I've tried googling for a solution to my problem but the combination of being relatively new to Ubuntu and not quite understanding the nature of the issue hasn't made it easy to find solutions to my problem. So I'm asking here...

I've been using Ubuntu (11.04) for a while and today decided I'd switch the language of my system from Dutch to English (my native language just sounds terribly lame in technological environments, so yeah...). So I went to system/management/language support and moved English above Dutch, then clicked "apply to the whole system". I rebooted and was asked if I wanted Videos and such to be renamed to their English equivalents (instead of "Afbeeldingen" etc), which I allowed it to do... The first problem arose here and I believe it to be causing my main issue or have the same cause.

The links to the downloads folder and such in the Places menu all became invalid. Apparently, Gnome or Nautilus (whichever manages the links in there) hadn't adjusted itself, so I removed the links. However, there were 3 stubborn ones: Home, Desktop and Computer

Opening them either returned that Nautilus did not have access to /home/marnick/Desktop and that it probably needed more rights or that file:///computer links are not supported. Something along those lines anyway, I can't check due to my bigger problem...

I was able to fix the Home and Computer links by removing /home/marnick/Desktop as root, allowing Nautilus to restore it (apparently, the transition from Dutch to English had screwed it up). However, the Desktop link refuses to work, always saying it can't find /home/marnick/Bureaublad (which is still the Dutch word for Desktop...). That's problem 1.

Afterwards, I edited the name tag for Ubuntu displayed on the grub screen and figured I'd reboot to check it. Before rebooting, I also edited something else that I can't quite explain aside from by giving you the guide I used: [http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/](http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/)
I was getting annoyed by always having to enter my password again right after boot for no apparent reason so I decided to disable that using the method that's been posted a dozen times over. 

Immediately after rebooting to apply those 2 changes, problem 2 showed up. It's just a little more annoying and reminds me very much of a similar mess I once had in Windows and never wanted to have again ( :mad: ): the login screen doesn't let me log in anymore

I boot, select Ubuntu (got a win7 dualboot, although the win7 is quite permanently broken/damaged and so I now rely on Ubuntu till I can get that fixed), wait a bit and then I get the login screen. It shows a window where I can click my name and avatar, expanding the box around it and revealing a password entry box, and another box saying "Other...". Here's the problem: normally, clicking either of them would bring up a password input box or some menu with special login options (I assume). What happens now is this: *click* *box expands* "bloop" *box shrinks* :confused:

I click my name/avatar, the box expands and then instantly shrinks, as if denying me my right to enter my password.

Going into the recovery mode and then doing some stuff that takes me to a text-only login screen reveals that my account is still working fine: when asking me for my username and password, it accepts my normal login and gives me the Marnick@Luxor command line that I'm familiar with, although that's quite useless with my limited knowledge of Ubuntu.

Doing apt-get install --reinstall ubuntu-desktop and reinstalling Nautilus (when I was still in my desktop environment, was hoping it'd fix the Desktop link) didn't fix anything.


Would anyone happen to know how to fix this, please? If you need any other info or if I need to clarify something, just ask... I wrote this in a bit of a rush and due to some loads of crap happening to me in RL (add this to the list) I'm in no mood at all to read my entire post again and again a dozen times to make it more streamlined, sorry for that... I'll explain anything that isn't clear, I'm just not going to re-write my entire post 5 times before even posting it...

Thanks if anyone can help and go easy on the commands please :P I'm not new to exploring computers and doing techy deep-going stuff but Ubuntu is all new to me, down to its very core

---

### Post by Faziri on 2011-09-22
Never mind, problem solved... Sorry, i'm not quite used to the fact that, if the system is screwed up, you can just boot the live cd and fix whatever could be wrong.

Apparently, I've once again got luck against me because the keyring disabler (which seems to be a very common way to handle the things) caused the login issue... As usual

---

