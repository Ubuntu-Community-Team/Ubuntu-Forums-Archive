---
title: "How do I enable the Unity desktop theme?"
date: 2012-06-01
forum: Desktop Environments
---

### Post by abefroman99 on 2012-06-01
How do I enable the Unity desktop theme?

:KSThanks:KS

---

### Post by Frogs Hair on 2012-06-01
Unity is the default desktop on 11.04 -12.04 and is displayed as Ubuntu in the login screen . When you login select Ubuntu 2D from the list by using the icon on the right side of the greeter box.

If Unity 2D is working run the following test in the terminal to see if you have Unity 3D support.```
/usr/lib/nux/unity_support_test -p
``` 

If 3D is supported login to Ubuntu and use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.```
unity --reset
```


Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu and see what happens.

---

### Post by 2F4U on 2012-06-01
What exactly do you mean, what version of Ubuntu are you running? Unity in the standard version of Ubuntu is enabled by default, so you should take a little bit more time to explain your problem.

---

### Post by DMGrier on 2012-06-01
So here is my question, what is the difference between Unity 2D and Unity 3D? I do not see any real difference.

---

### Post by Frogs Hair on 2012-06-01
> **DMGrier said:**
> So here is my question, what is the difference between Unity 2D and Unity 3D? I do not see any real difference.

Visual effects is the main difference. Unity 3D is actually a Compiz plugin and it possible to easily change icon size,panel and launcher transparency. I am just as happy to login to 2D unless I want to see the Compiz eye candy . I have not checked if 3D uses more resources than 2D but I suspect it does. With a desktop battery life is not a consideration. If I had a resource issue I would be using Lubuntu or Xubuntu.

---

### Post by DMGrier on 2012-06-01
Well I have ran 2D on my laptop and have not noticed any real difference when it comes to battery life, I am sure it does use some less resources but since I think it comes down to what task you are doing for battery I seen little difference between 2D and 3D.

---

