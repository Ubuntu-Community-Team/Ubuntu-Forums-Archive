---
title: "Using Ubuntu / Linux at school in Indonesia"
date: 2008-05-30
forum: Education &amp; Science
---

### Post by freedom10 on 2008-05-30
hello...
we are social studies teachers in Muhammadiyah 2 High School, surabaya, east java, indonesia, start using ubuntu in our teaching activity. but, we have lack of tutorial and another material about ubuntu and linux as general.
can anybody help us to make our ubuntu great tool to teach?
here are our addres:
SMA Muhammadiyah 2 Surabaya
Jl. Pucang Anom 91
Surabaya-East Java
Indonesia

---

### Post by thisismalhotra on 2008-05-31
Did you try edubuntu I think that is more tuned towards education an school stuff. As of release 8.04 edubuntu is not a special distro but an add-on cd in ubuntu which you can download and install.

If you google there is enuff guides online to start everybody on ubuntu. Thats how we all started you as we all were windows user at some point in history .. LOL

This probably would be a good start : -

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Also, there is a help menu within ubuntu itself ... Good Luck

---

### Post by Prospero2006 on 2008-06-01
Hello there, 
I'm a teacher in San Antonio, Texas and I just completed my first year teaching full time in a Ubuntu lab. Ubuntu is powerful in the classroom.

Here's my school homepage:
[http://www.neisd.net/imak](http://www.neisd.net/imak)
Here's a link that explains a bit more about our Linux Labs
[http://www.neisd.net/imak/computerlabpage/](http://www.neisd.net/imak/computerlabpage/)

Here are some tips:
      -Set up Kiosktool under Kubuntu. 
       (This will keep the kids from making changes to the system.)
      -Have everyone log into the machines using username: student
      -Set up 'iTALC'  (Tutorial Link Below)
        -http://ubuntuforums.org/showthread.php?t=702437
      -Use the firefox extension 'Public Fox'
        -This will allow you to control the web browser.
      -Create one machine that works and then clone it
       using dd and netcat. (All of my computers are exactly
       the same. So, this type of disk imaging is quick and
       easy.)
      -Set up passwordless authentication over ssh for the superuser
       on all computers across the lab. 
            -This will allow you to execute commands on every machine
             in the room at once from the master computer. 
                  -For example, I can run 'poweroff' on every
                   machine in the room by running a script that
                   runs ssh 10.43.231.X 'poweroff'  (X is then
                   incremented by 1 until X=30) In this way,
                   10.43.231.1 through 10.43.231.30 are all contacted
                   and the command 'poweroff' is given.
                  (It's pretty cool at the end of the day when I run
                   it and the whole lab shuts down.)
        -Set up **apt-cacher** and use one machine in the room as 
         a central repository. In this way, you'll only have to download  
         packages once in order to upgrade all of your computers. Client 
         computers, if configured correctly, will check the local 
         repository first for packages and then download from the internet
         if not present.

  -I know that's a lot to throw at a teacher who is thinking about setting
up Ubuntu, but if you contact me I will help. The kids love it.

---

