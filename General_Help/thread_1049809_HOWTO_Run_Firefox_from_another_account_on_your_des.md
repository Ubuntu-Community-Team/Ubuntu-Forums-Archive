---
title: "HOWTO: Run Firefox from another account on your desktop"
date: 2009-01-24
forum: General Help
---

### Post by Yashiro on 2009-01-24
This example is little basic but perhaps it will help someone realise how flexible Unix and X is. 
The second account referred to in this post can be on your local machine or on any Unix compatible machine with X, potentially.

Let's assume you think Firefox is behaving oddly and you want to test things out using a clean environment.
[So, create a second user account on your Ubuntu system](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu). Call him *bob*. Assign him a password. 

Log into your regular desktop and open a terminal.(run gnome-terminal)

Enter:
> xhost +
> su - bob

Input the password when asked. You could use *ssh -X bob@someremoteloaction* and log in to a remote PC too of course.

You are now logged in as Bob! Wow I am Bob. Bob is a cool guy but his fonts will suck. Anyway lets carry on.
> export DISPLAY=:0.0
This tells bob's X to send it's output to :0.0. :0.0 is your screen.(<your address>:0.0)

Type:
> firefox &
Bob's pristine Firefox and all related profile data is running on your desktop. You should feel a bit dirty at tainting Bob in this way. It will pass, don't worry.
When you've had enough. Close the window.
> exit
> xhost -

I realise this is a bit oversimplified but I hope someone might find this useful. This should work for all X apps. 
Be careful though, because now you will want to know about gnu/screen.

Or even [http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by dcstar on 2009-01-25
> **Yashiro said:**
> This example is little basic but perhaps it will help someone realise how flexible Unix and X is. 
The second account referred to in this post can be on your local machine or on any Unix compatible machine with X, potentially.

Let's assume you think Firefox is behaving oddly and you want to test things out using a clean environment.
[So, create a second user account on your Ubuntu system](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu). Call him *bob*. Assign him a password. 

Log into your regular desktop and open a terminal.(run gnome-terminal)
........

Or simply use the "Switch User" function and log on as the other account.

---

### Post by fixitdude on 2009-01-25
You can use this to protect against Adobe Flash exploits and things like that. You can set up Firefox on that user to have Adobe Flash and JavaScript on as default and browse without worrying about your main account and it's information being compromised if a exploit hits you.

Flash had a few exploits lately.

It may be easier just to log in locally via SSH as that user and then start Firefox over the SSH connection, like this:

ssh -2 -Xc blowfish bob@127.0.0.1
(then enter password for bob)
firefox &

Now the browser pops up and works like it always does except everything is restricted to "bob"s account.

---

### Post by Yashiro on 2009-01-25
[QUOTE="dcstar"]Or simply use the "Switch User" function and log on as the other account.[/QUOTE]This is not the same. Especially so with some video drivers.

[QUOTE="fixitdude"]It may be easier just to log in locally via SSH as that user and then start Firefox over the SSH connection, like this:

ssh -2 -Xc blowfish bob@127.0.0.1
(then enter password for bob)
firefox &[/QUOTE]

I did it step by step so people can see what's going on. Of course when they get clever it can all be condensed to scripts ;)

---

### Post by mb_webguy on 2009-01-25
While this works well as an illustration of the versatility of Linux and X, it's not really the best way to go about running a clean or alternate version of Firefox.

You could simply run "firefox -ProfileManager" in the terminal and create a new profile.  This is useful when you're having a problem and want to check if it's due to extensions you have installed.  The only difference between this and the method in the original post (other than this is *much* simpler) is that the two profiles will use the same plugins, whereas running Firefox from another account may not, depending on where those plugins are installed.

---

### Post by fixitdude on 2009-02-09
> **mb_webguy said:**
> While this works well as an illustration of the versatility of Linux and X, it's not really the best way to go about running a clean or alternate version of Firefox.It's great. I can open a completely new Firefox while my current Firefox is still open.

I can browse on "dangerous" sites with JavaScript on and Flash and don't have to worry about giving any access to any of my main files since it is on a separate user account that has nothing important in it's files.

An attacker would have to somehow transverse into my main account to do any damage, and that's very hard to do on Linux.

If the graphical settings for the new Firefox user are set differently, the browser will look sort of different and I can easily tell which one is which.

You can also have alternate accounts on sites such as google mail and have them open at the same time.

When you use a new profile, the old profile closes.

---

### Post by Yashiro on 2009-02-09
Indeed, if you're really paranoid you could create a guest user with data stored in tmp or even on a tmpfs mount.

---

### Post by KeyserSoze93 on 2009-02-10
Put this in your launcher:
```
gksu -u bob firefox
```
Where bob is your other user.

Just remember, firefox will only let you open on instance, so I doubt you'll be able to have your firefox and "bob"'s firefox open at the same time...

---

### Post by Yashiro on 2009-02-10
That's where you fail to grasp what's going on. You do indeed run both simultaneously.

---

