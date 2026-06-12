---
title: "COMPIZ Messed up"
date: 2011-05-11
forum: Desktop Environments
---

### Post by priyanka_hdp on 2011-05-11
when i install compiz (ccpm) and apply a 3D cube Desktop changer.,
then my desktop messed up.now it shows windows with NO Title Bars

how to fix it friends.?

:confused:

---

### Post by sikander3786 on 2011-05-11
I hope this is Unity and Ubuntu Natty we are talking about. If correct, I hope these links would help you.

See the Unity Reset section to get your Window Decorations.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

And for enabling cube,

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by cvielma on 2011-05-11
Hi. 

You could also try restarting compiz:

Alt + F2 -> compiz --replace

Hope it helps.

Best regards,

---

### Post by priyanka_hdp on 2011-05-13
thanks dude..........those posts are very helpful to me....

---

### Post by pritam_par on 2011-08-10
To enable  the cube with Unity follow the process below


1.In compiz setting manager disable these plugin:
             i) OpenGL
              ii) Composite
              iii) Ubuntu unity plugin
             iv) Desktop wall.
     

2. Now enable these plugins sequentially.   
          i)OpenGl
         ii)Composite
        iii)Desktop cube 
        iv)Rotate cube
        v)Ubuntu unity plugin.

There may be the possibilities that  after enabling the desktop cube with Unity maximize and minimize button  disappear or you are unable to move your window. To get back all these  function, in the **compiz manger** select the option "**Move Window**" and " **Window Decoration**".

---

### Post by twengg on 2012-09-17
Maybe this will help someone else: 
If nothing else works, install ubuntu tweak (ctr+alt+t then sudo apt-get install ubuntu-tweak)
Then go to admins>>Desktop recovery>>reset
I did this after unity --reset and re-installing unity failed, and probably everything else I read off the net.

---

### Post by overdrank on 2012-09-17
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

