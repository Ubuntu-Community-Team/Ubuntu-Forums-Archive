---
title: "Scanning"
date: 2005-03-20
forum: Desktop Environments
---

### Post by cajunaggie on 2005-03-20
Does anyone know of any good scanning software?

---

### Post by WW on 2005-03-20
I bought Vuescan ( [http://www.hamrick.com/](http://www.hamrick.com/) ) to use on a windows machine quite a while ago, and since then I have used the linux version (on both Libranet and Ubuntu warty) and it has worked just fine.  You will probably get some good suggestions for open source/free software, and you should try that first, but keep Vuescan in mind as good (but not free) option.

---

### Post by kleeman on 2005-03-20
xsane works for me  :)

---

### Post by wylfing on 2005-03-20
It has admittedly been some time since I installed it, but my print server, which runs Debian, uses xsane to scan with an HP OfficeJet G85. As I recall, I did absolutely nothing besides 'apt-get install xsane'. Works great, and it's very easy to understand how to use.

---

### Post by cajunaggie on 2005-03-26
Xsane doesn't support my scanner. Any suggestions on fixing this or for other software?

---

### Post by az on 2005-03-26
What model is your scanner?

---

### Post by cajunaggie on 2005-05-02
HP Office Jet t45

---

### Post by kleeman on 2005-05-03
Try installing the hplip package, according to this page

[http://hpinkjet.sourceforge.net/productsmf.php](http://hpinkjet.sourceforge.net/productsmf.php)

scanning is supported with the t45. I used to have one of these and remember it as
difficult under linux but I did get the scanning going eventually

---

### Post by loser72555 on 2005-05-03
absolute total newbie here.  I untarred/unzipped the files.  I find several .sh extensions, but have NO freaking clue as to how I am to "install" this mess.

any idiot proof instructions?

---

### Post by kleeman on 2005-05-04
For warty things are complicated with hplip. For hoary there are packages in the universe repository so there all you need do is "sudo apt-get install hplip" at the commandline OR use synaptic its easy ;-)

---

