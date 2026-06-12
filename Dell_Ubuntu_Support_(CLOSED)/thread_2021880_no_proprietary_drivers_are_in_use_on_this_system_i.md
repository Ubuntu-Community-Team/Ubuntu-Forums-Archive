---
title: "no proprietary drivers are in use on this system in ubuntu 11.04"
date: 2012-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lokesh1729 on 2012-07-09
I am using ubuntu 11.04.I have installed compiz and ccsm.when i installed compiz my system slows down.i checked in system-> Adminstration->Additional drivers.It shows no proprietary drivers are in use on this system.So , I installed fglrx and fglrx-amdccle.but it doesn't work.my graphic card version is "intel hd graphics 3000".

---

### Post by QIII on 2012-07-09
Fglrx is for AMD/ATI cards and you should remove it.

For intel graphics, there is no specific additional driver, which is why none was offered.

---

### Post by lokesh1729 on 2012-07-10
removal of fglrx can cause any problems... I am afraid of destruction of os
please help me sir

---

### Post by QIII on 2012-07-10
Do you have an AMD/ATI graphics card?

---

### Post by lokesh1729 on 2012-07-10
i am using dell inspiron n5050. I have intel hd graphics 3000.when i enter command lspci | grep VGA   
output:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by QIII on 2012-07-10
Then removing a driver for hardware you do not have will do no harm.

How did you install the driver?

---

### Post by lokesh1729 on 2012-07-10
I have another laptop acer aspire 4535 with ubuntu 9.10. when i go to system-> Administration->Additional drivers it shows ati graphics drivers.Then i installed packages fglrx.But now i have dell inspiron n5050 i downloaded fglrx package and installed it

---

### Post by QIII on 2012-07-10
If your n5050 does not have AMD/ATI graphics, you do not need the ATI/AMD driver.

---

### Post by lokesh1729 on 2012-07-10
Sir i have one small doubt.... when i search on google about my dell inspiron n5050 laptop it shows intel hd graphics 3000.Is my laptop have intel graphic card.when i enter command lspci | grep VGA 
output:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
is my laptop have intel graphics card

---

### Post by QIII on 2012-07-10
Yes.

That means you do not need the fglrx driver, which is for AMD/ATI graphics.

---

### Post by lokesh1729 on 2012-07-10
Sir, then i remove fglrx.... when i install compiz-fusion-icon my effects has gone.before installing it i have some effects.can i remove compiz-fusion-icon

---

### Post by lokesh1729 on 2012-07-10
Before installing compiz-fusion-icon i have some visual effects.but when i installed it my system structs.can i remove it

---

### Post by QIII on 2012-07-10
I am not sure if we are having a language issue here or not.
 
 You do not need the fglrx driver because you do not have an AMD/ATI card.  I would advise uninstalling it.
 
 If you need to, you may reinstall compiz, the compiz manager and compiz-fusion-icon after removing the fglrx driver.

If you continue to have compiz related issues, start a new thread to ask for help with that.

---

### Post by lokesh1729 on 2012-07-10
Sorry for my language sir

---

### Post by QIII on 2012-07-10
No problem.  No need to apologize.   I understand that we may speak different languages.  I am trying to make myself clear.

We may have a language barrier that is making it difficult for both of us.

---

### Post by lokesh1729 on 2012-07-10
> **lokesh1729 said:**
> Sorry for my language sir
When i go to system->Administration->Additional drivers.No proprietary drivers are in use on this system

---

### Post by QIII on 2012-07-10
Have you removed the fglrx driver?

Even if it is installed, it is not being used because there is not AMD/ATI GPU.

But I would still remove the driver because it is unnecessary.

After you have removed it, you will still get that message because the Intel graphics don't use an additional proprietary driver.

---

### Post by lokesh1729 on 2012-07-10
I removed fglrx... i will reboot now sir.but what is the command to reinstall compiz....
sudo apt-get reinstall compiz
is above command correct

---

### Post by QIII on 2012-07-10
Please start a new thread referencing compiz in the subject line.

That way others will see it.  With the current subject line, nobody will know there is a compiz question here.

---

