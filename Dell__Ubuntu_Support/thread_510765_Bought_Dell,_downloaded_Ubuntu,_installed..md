---
title: "Bought Dell, downloaded Ubuntu, installed."
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by jagger27 on 2007-07-26
Problem with display.

I cannot view anything on my 22" Dell LCD. Luckily I had a dual monitor set-up. I can only see ubuntu on it. When starting up it shows the Ubuntu loading on both monitors, but when I log in it only shows on my Acer CRT 15". Also, i tried to download a driver from nVidia but Ubuntu said: "Could not open the file /home/jagger/Desktop/NVI&#8230;x86_64-100.14.11-pkg2.run." My video card is a nVidia GeForce 7300LE [http://www.nvidia.com/page/geforce_7300.html]("http://www.nvidia.com/page/geforce_7300.html")

Please help!


EDIT: The error message says something about character coding.

---

### Post by nichipet on 2007-07-26
You're trying to enable dual monitors on a Dell with Ubuntu or is it your main display that is not working? Just so I understand your situation. If it's dual monitors, I'm not sure about getting that to work on a Dell. I'm using a Dell Inspiron 1501 and can't get dual monitors to work. If it's your main display, I would think the nVidia drivers would work. What happens when you go into a prompt and try:

```
ls -l /home/jagger/Desktop/NV*
```

That will show us the permissions for the file, and if the file exists or not.

---

### Post by jagger27 on 2007-07-27
it says this....

jagger@Jagger-PC:~$ ls -l /home/jagger/Desktop/NV*
-rw-r--r-- 1 jagger jagger 11838502 2007-07-22 23:15 /home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
jagger@Jagger-PC:~$ 

And I would like to do dual monitor. But i would also like to see an image on it! :P It is my main display that isn't working

---

### Post by nichipet on 2007-07-27
If you disconnect the dual monitor, does the main display work? I assume it does. To possibly fix the error message:

```
 chmod 700 /home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

It does not have execute permissions and maybe the driver is trying to run the file (considering the filename ends with .run).

---

### Post by jagger27 on 2007-07-27
Disconnecting didn't work. My CRT is still the only one that will display an image.

I will try that command. Code didn't work, it said directory does not exist...

BTW, when I try to just run the file this is part of the message: 

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by nichipet on 2007-07-27
Ok, your main display does not work. What model computer is it, and if it's a desktop, what model is the Dell monitor? This is just so I can search the web for the models and see if a fix comes up somewhere.

On the code not working, I'm guessing you either moved or deleted the file first or you mistyped something. Just use copy/paste from here:

```
chmod 700 /home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

I used copy/paste from your output for ls -l. If ls -l can find the directory and file, then chmod can as well. Also do this and give us the output from it:

```
file /home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

That will tell us what type of file it is (ie. a .doc file reports itself as a Microsoft Office Document).

---

### Post by jagger27 on 2007-07-27
I have a Dell Dimension E521 with [http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-5205]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-5205") << that monitor. I will try the command prompts now.

First code i copied and no errors popped up but nothing happened. 

the second one gave me this:

....14.11-pkg2.run: Bourne shell script text executable....

And my main display does work. I use it on my Vista Dual boot.

---

### Post by pbcartwright on 2007-07-27
type
chmod 777 /home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run:

then ./home/jagger/Desktop/NVIDIA-Linux-x86_64-100.14.11-pkg2.run

that will execute that file. You want to install that program, but it needs to be executable first, then you run it to install the driver.. read the README that comes with the driver.. You get the readme from the same page where you download it.

---

### Post by jagger27 on 2007-07-27
omg, this is so confusing! I copied the codes in and all it gives me is an error! wth am i doing wrong?!?!?

---

### Post by nichipet on 2007-07-27
What is the error? We can't troubleshoot it if we don't know what it says.

---

### Post by scotty32 on 2007-07-27
if you have an NVidia card, couldnt you just install via the repositories?

---

