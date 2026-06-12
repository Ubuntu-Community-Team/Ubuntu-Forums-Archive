---
title: "[SOLVED] Dell Vosrto 200 mini help needed"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GabrielsHorn314 on 2008-10-07
Hey guys, I have had ubuntu on my laptop for a while now, but since buying a desktop i am having a big problem getting it to work. I was wondering if anyone else was having problems with the dell vostro 200 mini. Ubuntu installs fine, bet when loading it will sit at the loading screen for several minutes then shuts off. I have tryed to create a virtual machine that boots from the ubuntu image file, but once it loads the main ubuntu screen where I select the language, it gives me an error message that the virtual machine must be shut down. Any help would be greatly appreciated.

---

### Post by Partyboi2 on 2008-10-09
Try removing the splash screen and see what it is doing before it turns off. You can do this by pressing F6 and removing the word "splash" if you have not installed yet. If you have installed ubuntu. Then boot ubuntu and when you see grub loading... at the top of the screen press ESC then highlight the kernel you are going to boot into and press "e" then highlight the line that starts with kernel... and press "e" again the remove the word "splash" then press "enter" and finally "b" to boot.

---

### Post by GabrielsHorn314 on 2008-10-09
I started from scratch today , and it never gets to the splash screen. After putting the ubuntu disk into vista, it takes a few minutes then asks me to reboot. I select reboot now, then it takes me to the screen where i select either vista or ubuntu. I select ubuntu, then it asks what time of instalation i want. No matter what type I pick , it goes to the loading screen and the orange bar moves back and forth, after a few minutes it shuts off and send me back to the beginning. I never actually get to the splash screen and since its not installed I can't press F6 to remove it when grub loads. Any other suggestions?

---

### Post by Partyboi2 on 2008-10-09
>  it goes to the loading screen and the orange bar moves back and forth This is the splash screen.
Are you trying to install ubuntu inside vista (using the wubi installler) or on its own partition?

---

### Post by GabrielsHorn314 on 2008-10-09
O, sorry. I am trying to set it up on its own partition. During this screen I tried pressing F6 and nothing happened.

---

### Post by Partyboi2 on 2008-10-10
Just to clarify:
Are you pressing F6 when you see the splash screen? Or at the main menu? You should be pressing F6 at the main menu see the picture below.
You will only see this main menu if you are using the live cd and have not installed yet. If you have installed ubuntu and it has asked you to reboot. When it reboots you will see the grub menu screen straight away or you will see grub loading.... and will need to press Esc to see the actual grub menu. The grub menu will look something like the 2nd picture below. If you see the grub menu, 
highlight the kernel you are going to boot into and press "e" then highlight the line that starts with kernel... and press "e" again the remove the word "splash" then press "enter" and finally "b" to boot.

---

### Post by GabrielsHorn314 on 2008-10-10
here what it says:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell(ash) Enter 'help' for a list of built in commands

(initramfs) [113.338194atal.00 revalidation fail]

it does this about 10 times while saying revalidation failed, but with different numbers. then it shuts off and brings me back to the original screen.

---

### Post by Partyboi2 on 2008-10-10
Go into your bios and try changing sata mode from ide to raid.

---

### Post by GabrielsHorn314 on 2008-10-10
If you wouldn't mind explaining to me how to do that, i would really appreciate it.

---

### Post by Partyboi2 on 2008-10-10
I just re checked and it doesn't look like you have raid support in your bios. So scrap that idea. Instead try using  all_generic_ide as a boot option. You can add this like the the same way you removed "splash" except instead of removing splash add
```
all_generic_ide
```

---

### Post by GabrielsHorn314 on 2008-10-11
thanks a lot, that worked. finally no more vista.

---

