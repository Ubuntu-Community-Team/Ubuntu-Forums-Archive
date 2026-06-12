---
title: "C not working due to key mix up."
date: 2009-01-03
forum: General Help
---

### Post by Liliitha on 2009-01-03
Errr... help...

> £include <stdio.h>

int main()
{
printf(@Hello, world#n@);
return 0;
}

> first.c:1: error: stray ‘\302’ in program
first.c:1: error: stray ‘\243’ in program
first.c:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘<’ token
first.c:5: error: stray ‘@’ in program
first.c:5: error: stray ‘#’ in program
first.c:5: error: stray ‘@’ in program
gaurdian@ubuntu:~$ 






For some reason the I cant make the quotation marks and other various keys, instead they are other symbols which is messing everything up... :(

---

### Post by mali2297 on 2009-01-03
Which editor do you use? Does it show quotation marks correctly? Have you imported the file from elsewhere?

---

### Post by Liliitha on 2009-01-03
Actually... now I just figured out it is for my entire system...  I noticed it when I was trying C but now I find that I can't type the same keys on anything in the computer.  I switched to my windows OS on the other partition and the quotations and other keys worked just fine so it isn't the keyboard.

---

### Post by Tim Sharitt on 2009-01-03
I may be your beyboard layout. You can check in Systerm > Preferences > Keyboard to make sure you have the correct one enabled.

---

### Post by ByKeLaO on 2009-01-03
Go to System->Preferences->Keyboard and click on the Layouts tab. Choose the layout that corresponds to your keyboard.
EDIT: Beaten again.

---

### Post by Liliitha on 2009-01-03
AH ok thanks so much.  I was scared I would have to reinstall something :shock:

---

