---
title: "installing using source code"
date: 2009-06-15
forum: General Help
---

### Post by xixpsychoxix on 2009-06-15
I am trying to install GTK+ from source code and the instructions i found tell me that i have to gain root access to install them; unfortunately, when i use su to try to gain access, it says that authentication failed. the password that i need to use should be my login password since i am the one that installed the system, correct? or do i need to put in some other thing that i know nothing about? I dont understand alot about Ubuntu yet, just started using it a few days ago.

---

### Post by Bigtime_Scrub on 2009-06-15
Ubuntu uses "sudo" not "su -". The password you set up should still be the same.

---

### Post by Polaris96 on 2009-06-15
You've inadvertantly stumbled into one of the nasty little secrets of "sudo" distros.  Although, you CAN, in fact, use sudo for most all of the build/compile/install work you're contemplating, it's a pain to type "sudo" in front of everything.

Also, sometimes sudo just doesn't have enough priviledge to get you what you need.  I have run into more than one situation where even sudo won't push a command.  Here's the answer:

1.  Open a terminal
2.  enter [edited.  See: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) ]
3.  when prompted, enter your normal password as if you were doing sudo
4.  enter and retype the root password when prompted

That's it.

Now, you can type "su" and get root access by entering the root password you just created.  You can also log in as root, this way.

Happy compiling!

---

### Post by estyles on 2009-06-15
@Polaris - first off, it's against forum guidelines to tell users how to enable the root user, because it's a) generally unnecessary and b) potentially dangerous for users that may not know what they're doing.

Second, it's much more reasonable to just do "sudo su", type your own password, then do what you need to do as root, then logout.

---

### Post by sdennie on 2009-06-15
> **Polaris96 said:**
> You've inadvertantly stumbled into one of the nasty little secrets of "sudo" distros.  Although, you CAN, in fact, use sudo for most all of the build/compile/install work you're contemplating, it's a pain to type "sudo" in front of everything.

Also, sometimes sudo just doesn't have enough priviledge to get you what you need.  I have run into more than one situation where even sudo won't push a command.  Here's the answer:

1.  Open a terminal
2.  enter [edited.  See: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) ]
3.  when prompted, enter your normal password as if you were doing sudo
4.  enter and retype the root password when prompted

That's it.

Now, you can type "su" and get root access by entering the root password you just created.  You can also log in as root, this way.

Happy compiling!

1) Don't post information about how to enable root logins.
2) Using: "sudo -i" is just as good (in fact better) than "su -"
3) You should never build software as root.  In fact, you shouldn't even install it using "sudo make install" but instead use fakeroot to verify that it's going to install in a sane manner and then tar up the fakeroot and install that way.  Or, better, use checkinstall to make a proper package.

---

### Post by Polaris96 on 2009-06-15
1. @the men in black:


I'm confused:  This is the link you're citing, I believe  (forgive the lack of fancy "Quote" screen)

" Forum policy on log-in-as-root tutorials
Policy
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

Users posting such tutorials after this announcement will be given a warning or infraction at the discretion of the staff."


I didn't, however, break this rule.  

One will note the absence of any reference to "graphical login," or instructions on adding such an account to a GUI, or how to enable an autologin FOR a GUI anywhere in my directions.  This is totally happenstance, by the way.

I don't really see why anybody would need to log into a GUI as root.  That's the only reason I didn't say how.  I did NOT deliberately omit such instructions.  But, the simple fact that I did absolves me of guilt under that rule as it's wrtten.  

Nonetheless, even though I didn't get the memo, I'm suitably admonished and will never ever ever ever ever do it again.   please don't tell dad...

It's pretty odd for an open source forum to deliberately restrict information.  Your point about compiling code as root is very well made, though.  I'll take a slap on the wrist for not catching that one much more seriously than this sillyness of "don't tell people how to use their own OS"




2.@ xixpsychoxix:  Best of luck, friend.  The other guys are 100% right about not using any root priviledges until you do the final install.  That said, I think you SHOULD learn to use all the functionality you have - even the evil forbidden magic...  Bear in mind, I ALSO think you should completely crash your deck a few times.  It's always a good education 'cause you learn better when it's painful.  Root terminal is very seductive and has to be used with discretion.

If you want to keep going with the source builds, check out the folks at Encap ([www.encap.org](www.encap.org))  who have a really nice management utility for source builds.  So far as plucking the forbidden fruit goes, I don't want to get in more trouble, so I WILL NOT give you any addresses for other forums.

By the way, the usual way we install binaries is with .deb packages.  They're named for Debian, which is the open source, open minded distro that ubuntu is built on.  They say Debian is free, like freedom is free (and beer, too)  Happy hunting :)

---

### Post by sdennie on 2009-06-15
> **Polaris96 said:**
> Sorry about breaking the rules.  I'm suitably admonished and will never ever ever ever ever do it again.

It's pretty odd for an open source forum to deliberately restrict information.  Your point about compiling code as root is very well made, though.

Enabling the root account is like "voiding the warranty".  It's a fundamental change in how the system behaves and so editing posts about enabling the root account when alternatives exist is a way to help keep peoples machines in a predictable and consistent state.  The link I edited into your original post explains this in detail.

---

### Post by sdennie on 2009-06-15
You must have edited while I was responding.

You didn't break the word of the policy, you broke the spirit of it.  If I were trying to give you a slap on the wrist or threatening to "tattle to dad", you'd have an e-mail titled, "You have received a warning on ubuntuforums.org" in your inbox.  ;)

Compare enabling the root account to something like, "Type this one command and replace the linux kernel with the hurd kernel" (with no instructions on how to revert back).  If we started to receive a huge volume of posts about such a non-standard configuration, I think it's not unreasonable for us to declare, "Thou shalt not instruct thy neighbor how to install the hurd kernel".

It's not a big deal.  You didn't know and didn't do it out of malice so I just edited your post with a link to the policy.

---

### Post by xixpsychoxix on 2009-06-15
well, since i really dont know jack crap about ubuntu yet, maybe i'll just reinstall windows... HA!!!!! Just kidding, but i've seen enough to scare me off of trying to install new stuff until i understand the system better. I hope there are good tutorials out there!!!

---

### Post by estyles on 2009-06-16
> **xixpsychoxix said:**
> well, since i really dont know jack crap about ubuntu yet, maybe i'll just reinstall windows... HA!!!!! Just kidding, but i've seen enough to scare me off of trying to install new stuff until i understand the system better. I hope there are good tutorials out there!!!

There are *lots* of good tutorials out there.  And truthfully, building from source isn't as hard or as daunting as it seems.  Please check the repositories first before trying to build from source - you'd be surprised at how much stuff is in there.  I wasted a lot of time trying things the hard way as an Ubuntu newb because I just figured that this was Linux and things had to be done the hard way.

And if you can't find it in the repositories, you still might be able to install something "the easy way" by finding a .deb, which is essentially as painless as a Windows setup.exe, but without 15 "are you sure you want to continue" screens, and with less chance of malware (not 0% chance - you always take a risk when it's not from the repos, but much lower chance than on Windows).

---

### Post by xixpsychoxix on 2009-06-16
well the GTK+ package is almost certainly not in the repositories...  i looked about fifty times and did numerous searches. as for a package, i didnt find one anywhere as of yet, but ill keep looking

---

### Post by estyles on 2009-06-16
Did you try libgtk?

Gnome is built on gtk+, so most of the libraries are included in a default install.  If you're looking for development libraries, it could be there under something like libgtk2.0-dev.  I haven't done any development under Linux yet and don't have the ability to check the repos right now, but I find it hard to believe that the gtk+ libraries are not there.

If you're planning to do development, you might want to check out Eclipse - it's primarily aimed at enterprise java devlopment, but there is a C++ IDE included as well.

If you're not planning on doing development, then is there some other reason that you need to build gtk+ libraries from source?

---

