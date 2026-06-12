---
title: "delete partiotion ubuntu was installed in (after installation failure)"
date: 2009-03-06
forum: General Help
---

### Post by ScroogeMcDuck on 2009-03-06
Hello Ubuntu users,
I recently tried to install ubuntu to my computer (dual boot) with the live-cd, but for some reason it miserably failed. It was very weird. The installation went normally, except that I needed to type noapic at the bootcommandline because it kept hanging at "starting bluetooth", and when I rebooted, grub launched normally to the screen where you choose your OS, but then I got a message that there was an unclean shutdown, and then it checked the drives and blablabla, error error error. But I think it comes down to that the installation went drastically wrong. Thankfully vista is still working normally.

But anyway, I want to delete the partition (sda5) ubuntu is in now (and later reinstall it), but I have a question before that. because I read a lot of things about people saying that the mbr of windows would be overwritten or something during installation. So my question is: if I delete that partition, will I be able to still boot Vista?? Because I really don't dare to delete the partition without knowing that, since I practically can't do without a computer for a day.

Thanks in advance, hope I get an answer soon,
Scrooge.

---

### Post by namegame on 2009-03-06
Assuming you can still boot into Vista, I would download EasyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It is an easy way to restore the Vista Bootloader. After you have it restored, you can delete your uneeded partition from within Vista using "Computer Management."

I hope this helps. :)

---

### Post by ScroogeMcDuck on 2009-03-06
Thanks a lot, I'm gonna try it right away.

---

