---
title: "Administration settings with GUI"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Behel on 2005-05-16
I am having problems to access some GUI settings in System->Administration under Gnome. In particular: *Users And Groups*,* Share Folders*, *Networking*, and  *Time and Date*. This becomes more and more annoying, especially not being able to access Network settings.

To be more precise, after asking for my password and typing my CORRECT password, it loads the GUI but immediately show this message in a window:

"The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key"

I then have to click on "Close" and the GUI vanished... What is annoying is that after, if I want to start again, it doesn't not ask me for my password anymore but simply loads the GUI and then the previous message.

Is there any command that loads the differents GUI from the terminal so that I can check if it really works?
I have read a thread dealing partially with this problem but it did not solve mine.

Any help?

---

### Post by Behel on 2005-05-16
Continuing my monologue...

I have  logged in as root in Gnome and tried also to access *Users And Groups*,* Share Folders*, *Networking*, and  *Time and Date*. The same problem came. Same error message(!) without asking for any password...

Am I the only one who suffers of this problem??!!

---

### Post by Rodrigo on 2005-05-16
The only thing that I can come up with is: did you add your user to the sudoers file?, if you didnt DO IT!, DO IT NOW! 
If so... when you want to change the network file (and prompt for a pass) are you typing the root pass or your USER pass (thats the one you have to use after you add yourself to the sudoers file).
(even though its weird that you say log as root to Gnome and didnt work).

Try some search and dont panic  :grin:

---

### Post by Behel on 2005-05-16
Thank you Rodrigo for you reply,

Yes I am using my username password. Otherwise the window doesn't even load and ask kindly again for my password.

I have edited my sudoers file and now it looks like this

[I]Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
%admin	ALL=(ALL) ALL
%wheel ALL=(ALL) ALL[/I]

I think it should be ok (just think...).

What is weird (as you say) is that I can access *Printing, or Synaptic Manager, Login Screen Setup, Device Manager Printing and Ubuntu Update*.

So I will continue reading here and there some possible info...

Does anybody know a way to load the Networking GUI (for example) from the terminal?

---

### Post by Behel on 2005-05-17
I have typed in the terminal: *sudo network-admin*
then entered my password and I still have the same problem as with the GUI...

](*,) 

I have read this related thread a few days ago and left a message. 

[http://www.ubuntuforums.org/showthread.php?t=21629](http://www.ubuntuforums.org/showthread.php?t=21629)

There is maybe an answer there but need some help to decypher it... What can be the problem with .gksu.lock?
According to the thread, the problem was solved because: "It was PPP config that messed up the panel...works now =)". What should I do?

---

### Post by tread on 2005-05-17
Hmm .. try deleting the .gksu.lock file .. its in your home directory. (when I say delete, I mean rename, then if everything works fine delete it)

---

### Post by Behel on 2005-05-17
I renamed that file then tried to open this Networking window but still the same problem... Then another popup saying something like "child exiting status 127". Then the .gksu.lock file was back. FYI this file seems always empty for me when I open it in an editor...
Thanks for your help.

Still looking for the holy answer...

---

### Post by Rodrigo on 2005-05-17
Why dont you... re installing ubuntu?
(hey, its just a suggestion   :razz: )

keep searching the holy answer and tell us if you succed!

---

### Post by Behel on 2005-05-18
... this is what I'd like to avoid absolutly. It took so much time to tweak Ubuntu so that I can access my network drives at work, the windows printers etc... And now it look really nice... except this problem which I thought was minor problem and could easily solved...
maybe I will reinstall everything if really nobody have a solution... It looks a lot like a Windows solution, doesn't it?

Just a questions then: Will all my documents and settings be erased? or Are they preserved like with Windows?

*EDIT*
I change my password with *passwd* and after trying to run Network-admin again I had this error:

Failed to run network-admin:
Child terminated with 219 status

Any idea?

Thanks for all your help

---

### Post by tread on 2005-05-18
Have you tried running it in the console? Like start gnome-terminal, and type 

sudo network-admin
That should tell us if its a gksudo or sudo problem.

---

### Post by Behel on 2005-05-18
Hey maybe some improvement... I know probably more why I have a problem with the GUI. Here is what I typed in my root terminal in addition to the previous error window):

[I]root@Ubuntu:/etc/network # network-admin

(network-admin:7966): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

Is there any Master of Linux who knows what this means and I could do to avoid this error??

Hope this is helping...

---

### Post by Behel on 2005-05-20
After hours of frustration and search, I did not manage to solve the problem by myself and decided to reinstall everything remembering to me my not so far Windows era...

So I reinstalled it, this time connected to my university network which is a Windows network essentially. I did my first installation at home. Everything went like the first time except that I was this time proposed a hostname (since I was connected to the intranet). I decided to give it a try and continued with the installation. When it was done, I was happily surprised that I could access all my administration settings...

So is it possible that having a different hostname than the local network can prevent a user from accessing some administrative settings though I could access to internet and printers? If I had changed my hostname to the one proposed, would I have been able to access the settings?

Just a thought...  :? 

Well I can finally say that Ubuntu is a great great distro... can't wait to see Breezy!

Thanks to everybody who gave me support.

---

### Post by acorey on 2006-05-04
Wow, this is my first ever post on any linux forum.  

I had this same problrm and recieved this error message in the console about /etc/sudoers having the wrong permissions. 0660 instead of 0440, or somthing. I  googled it and found that I needed to ghange it to read only and now sudo works fine.  so does the GUI.

I hope this helps. All the best, AC

---

### Post by doina.babu on 2006-12-28
> **Behel said:**
> Thank you Rodrigo for you reply,

Yes I am using my username password. Otherwise the window doesn't even load and ask kindly again for my password.

I have edited my sudoers file and now it looks like this

[I]Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
%admin	ALL=(ALL) ALL
%wheel ALL=(ALL) ALL[/I]

I think it should be ok (just think...).



The problem is in the sudoers file. You don't have the root user privilege specification.
Add line for root:
root ALL=(ALL)ALL

---

### Post by linkinpark342 on 2007-02-14
I'm still having this same issue and have tried everything from the past posts but i can't get any headway. Has anyone figured out what the problem is. Do these really use gksu(do) for frontend becuase my gksu(do) works fine for everything else. Reinstallation is _not_ an option.

---

