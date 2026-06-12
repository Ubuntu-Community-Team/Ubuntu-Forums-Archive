---
title: "Grub Loading stage 1.5"
date: 2009-01-30
forum: General Help
---

### Post by DLeal on 2009-01-30
Hello I'm having a issue here. Recently I had installed Ubuntu onto a computer and when it asked me to restart the computer that when the problem began. When it restated and came back up, there was an error message saying, "GRUB Loading stage 1.5" what does this mean, and what can I do to fix this problem? Any help I would really appreciated it.

---

### Post by caljohnsmith on 2009-01-30
What is the exact Grub error you get? Is it Grub error 17 maybe? In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dcstar on 2009-01-30
> **DLeal said:**
> Hello I'm having a problem here, just earlier today I had installed Ubuntu onto a computer. After the installation was complete, I got this error message;  Grub Loading stage 1.5. What is the problem here? Any help I would really appreciate it.

When **exactly** did the message appear?

---

