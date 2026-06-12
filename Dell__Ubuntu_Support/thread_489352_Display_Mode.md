---
title: "Display Mode"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by Hilton on 2007-07-01
I have recently installed Ubuntu Linux, making my PC a dual boot computer with Window XP.  Windows XP screen display is perfect, but when I boot-up to Linux, the screen goes Black and displays this message :- 
[B]
1.Analog Input. Cannot Display this Video Mode.[/B]

After about 30 seconds, boot-up continues and then displays correctly (same as  Windows XP).

Can someone please tell me -

What does this message mean ?
Why is it shown as there seems no problem with the screen display ?
How to permanently get rid of this message.

Thanks.

---

### Post by khedron on 2007-07-01
After a bit of Googling, I found that (apparently) you can stop the error message by adding "vga=791" to the end of your kernel line. This is assuming you have a 1024x768 screen or bigger.

If you don't have a 1024x768 screen or bigger, could you please tell me your resolution?

If you do have a 1024x768 screen or bigger, you can make a change temporarily to see if it fixes the problem. At the GRUB menu highlight the Ubuntu line you use normally. Then press "e" to edit the entry (temporarily).
Then scroll to the line that begins
```
 kernel     /boot/vmlinuz-2.6.20-16-generic root=UUID.........
```or something like that.
Press "e" to edit that line.
Then press "End" to go to the end of the line and type " vga=791" (with a space in front). Press enter.
Then press "b" to boot that entry.

Does that fix it? If so, I will give you instructions on how to make the change permanent. If not, could you tell me the output of the following command:
```
sudo dmesg
```Thanks.

---

### Post by Hilton on 2007-07-02
Thanks for your help, but I still have a problem. I've only recently installed Linux and having used Windows for longer than I like to remember, I've never had to get involved with any sort of 'programming'. Your instructions are very clear, but you say 'From the GRUB Menu' - What is GRUB and where do I find it. I've hunted around and can't find anything remotely like it. Searching Help just gives a list of GRUB commands available. Not very helpful.

Incidentally my screen resolution is 1024x768. 

Thanks

---

### Post by khedron on 2007-07-02
Ok, first an explanation. In Linux there are two display modes: text-only and graphical. When you boot up, it starts in text mode and then switches to graphical mode when fully booted.

What I think has happened is that the text mode is not configured properly, so you can't see the booting messages. However when the computer goes into graphical mode, the display is fine, since the graphical mode settings are correct.

This error is not fatal - you can continue with it and the computer should work fine. However, if you want to get rid of the error message, read on.

When you turn on your computer there should be a menu asking you what you want to load - Ubuntu or Windows. This menu is the GRUB menu. It should look like the screen below (only with different choices).


[IMG]http://developer.skolelinux.no/%7Eknuty/bok/images/SLX15.png[/IMG]

Use the arrow keys to select your normal Ubuntu choice. If it is already selected, press down and then up again to turn off the countdown and reselect the line.
(The rest is copy-pasted from my last post to make it easier to read)

Then press "e" to edit the entry (temporarily).
Then scroll to the line that begins
```
kernel     /boot/vmlinuz-2.6.20-16-generic root=UUID......... 
```or something like that.
Press "e" to edit that line.
Then press "End" to go to the end of the line and type " vga=791" (with a space in front). Press enter.
Then press "b" to boot that entry.

Does that fix it? If so, I will give you instructions on how to make the change permanent. If not, could you tell me the output of the following command:
```
sudo dmesg
```
You can put the output into the file /dmesg-output using this command instead:
```
sudo dmesg >/dmesg-output
```

---

### Post by Hilton on 2007-07-02
Talking about a steep learning curve !!!

Adding 'vga=791' to the 'kernel' line works and the message is not displayed.

How is this made permanent?

Thanks

---

### Post by khedron on 2007-07-02
Yes, I'm afraid Linux can be a bit heavy on the configuration side if you get a problem. :(

What you have to do is slightly long, but I have written some commands that will do the job for you if you don't want to do it. If you just want the commands, skip to the end. (But where's the fun in that? ;))

EDIT: Do what geirha said below, not what I have said. That is, paste the following into your terminal:
```

sudo su
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sed -i 's/^# defoptions=.*$/& vga=791/' /boot/grub/menu.lst
update-grub
exit
```Now read the bottom of my post about restoring the original settings (just in case) and reboot.
END EDIT

Ignore all this:
[I]
If you want to do it manually, you have to edit /boot/grub/menu.lst , which is the file that tells GRUB what all the menu options are. First make a backup of the file by pasting this line into the terminal, entering your password at the prompt:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```The next command should open a text editor editing that file, once you have entered your password.
```
gksudo gedit /boot/grub/menu.lst
```Then change all the lines beginning with "kernel" so that they have " vga=791" at the end, apart from the one that says something like "memtest86+.bin".
Remember to put a space before you type the vga part so that it is separate from whatever else is on that line.

This will change your current choices to use the new setting. To make sure that all future choices will use that setting, find the line that begins with "# kopt=" and add " vga=791" to the end of that, too. Remember the leading space!

Then save the file (as /boot/grub/menu.lst if you are asked). Now read how to restore the original settings (at the end) and reboot to check that everything is ok.

 If you want to just paste the commands into the terminal, here is what you should paste. Type your password when asked for it.
```
sudo su
mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
cat /boot/grub/menu.lst.bak | sed 's/^\(kernel.*vmlinuz.*\)$/\1 vga=791/' | sed 's/^\(# kopt=.*\)$/\1 vga=791/' >/boot/grub/menu.lst
exit
```[/I][B]
To restore the original settings:[/B] if something has gone wrong, you won't be able to boot - you'll get an error message once you get to the GRUB menu. To restore the original settings, boot a Live CD and copy the <directory>/boot/grub/menu.lst.bak file to <directory>/boot/grub/menu.lst , where <directory> is the folder in which your system partition is in the Live environment.

If you have any questions about this, feel free to ask.

---

### Post by geirha on 2007-07-02
That will work, but the prefered way in ubuntu would be to change the defoptions line:
```

sudo sed -i 's/^# defoptions=.*$/& vga=791/' /boot/grub/menu.lst
sudo update-grub

```

update-grub will apply the defoptions to all kernel choices in the list

---

### Post by khedron on 2007-07-02
Nice, never thought of that!

---

### Post by Hilton on 2007-07-03
Thanks for your help. Works perfectly.

Now to sort out the scanner and webcam which don't work.

'Windows XP' might be a monster but Linux seems to be an 'ordinary' computer users nightmare.

---

### Post by khedron on 2007-07-03
Yeah, well at least it's moving in the right direction. This forum is a good example. Time was when posting a question on a Linux forum could easily just get a glib answer from a know-it-all. Ubuntu is a step forward in terms of this.

The real problem is that Linux is developed towards a power user who already knows all this stuff - not new users like you or me. Given time, I'm sure Linux will become as easy to use as Windows.

---

### Post by Hilton on 2007-07-04
Can't wait to leave Windows behind, but Linux has got to improve a lot before I feel comfortable enough to let go.

I daily encounter problems, like hardware not working or not compatible, unhelpful dialog messages which leave me wondering what to do next, programs with no Help or with options incomplete, even programs which give no guide as to their purpose. A quick glance at the descriptions in the Add/Remove Applications option shows that some programmers assume that all users are computer wizz-kids. We aren't.

In my past life - OK, well just a few years ago, I was a software tester, and a lot of the Linux software I have encountered so far, I wouldn't have passed because of being user unfriendly.

I hope the improvements don't take too long. :)

---

