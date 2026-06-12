---
title: "Gui for dpkg"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-11-22
i have almost entirely converted my brother to ubuntu, but i have one last hurdle, is there a gui available for dpkg ? if not i might have a go at making one in Realbasic, because its the only thing that has prevented me from having a 100% gui ubuntu system for my brother.

---

### Post by Sheco on 2005-11-22
synaptic

---

### Post by kperkins on 2005-11-22
Actually Synaptic is a GUI for apt-get, not dpkg.  :???: 
I don't know of a gui for dpkg--or the installation of individual debs that you've downloaded from someplace other than deb repositories. Synaptic certainly isn't it, and I think that that is what he's asking for.

---

### Post by SickTwist on 2005-11-22
Actually, there is a GUI for dpkg being developed for Dapper Drake. I just saw a screenshot within the last day or two but I can't remember where it was posted. I'll try to post a link to it if I can find it again.

But realistically, there is usually very little need (if any) to install deb packages by hand like that. There is already a **vast** quantity of software ready and waiting to be installed from the Ubuntu repositories (main, restricted, universe, multiverse) plus there is the backports project with more cutting-edge packages if 6 months is too long to wait.

---

### Post by kperkins on 2005-11-22
That's true, but, some packages will never get into the repositories--like Opera, for instance, and probably many others. I'd love to see that screenshot if you can find it.

---

### Post by cdsboy on 2005-11-22
i too would love a GUI for dpkg so keep us posted on your findings.

---

### Post by kperkins on 2005-11-22
Here's some links.  It's called gdebi.
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html)
Screenshot:
[http://www.whiprush.org/2005/11/gdebi_arrives.html](http://www.whiprush.org/2005/11/gdebi_arrives.html)
Screenshots and debs:
[http://people.ubuntu.com/~mvo/gdebi/](http://people.ubuntu.com/~mvo/gdebi/)
sounds good.
If I didn't need a fairly stable system I'd upgrade to Dapper now just for that.  I am going to try it on breezy, though.

---

### Post by darknuala on 2005-11-22
Currently there is:
[http://www.jamyskis.adakist.com/gkdpkg.htm](http://www.jamyskis.adakist.com/gkdpkg.htm)
dselect is a curses GUI for dpkg.

Not really a GUI, but the closest thing.  I cannot vouch for either of them.  Running sudo dpkg -i file.deb in a terminal is just as fast as opening a GUI program, and waiting for it to load, then do whatever you need it to do.

I did create a cheat-sheet of terminal commands that I used most frequently until I realize you can have the terminal remember your last commands that you've typed.  I usually scroll through for a few secs until I see my sudo dpkg command, and just change the filename to whatever it is that I am installing.

---

### Post by kperkins on 2005-11-22
gkdpkg installed a package with unmet dependencies and couldn't display what they were, in the window it opened up for that, I don't believe it's ready for prime time, yet, but it's a good start.  I'll try porting gdebi when I get a chance.

---

### Post by ranf on 2005-11-22
[QUOTE=darknuala]I usually scroll through for a few secs until I see my sudo dpkg command, and just change the filename to whatever it is that I am installing.[/QUOTE]
Try Ctrl+R then type part of a command you typed before.

---

### Post by SickTwist on 2005-11-23
[QUOTE=kperkins]Here's some links.  It's called gdebi.
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html)
Screenshot:
[http://www.whiprush.org/2005/11/gdebi_arrives.html](http://www.whiprush.org/2005/11/gdebi_arrives.html)
Screenshots and debs:
[http://people.ubuntu.com/~mvo/gdebi/](http://people.ubuntu.com/~mvo/gdebi/)
sounds good.
If I didn't need a fairly stable system I'd upgrade to Dapper now just for that.  I am going to try it on breezy, though.[/QUOTE]

Congrats you found it! :)

That's exactly what I was talking about. I still can't remember where I originally saw it posted--guess I was too busy daydreaming about the upcomming Dapper goodness.

---

### Post by kperkins on 2005-11-23
Yep I found it, but there were way too many dependencies that I would have to take care of, and the first one broke my system,  (not irrevokably :D) so I'll wait 5 months, I think.

---

### Post by Burning Bronx on 2005-11-23
Just installed gdebi ^_^ If you don't mind my language - it's the shit. If you do, then... It's the ****. I haven't had any problems using the dpkg but this little tools is so much smoother. It would be a shame if they don't implement it.

---

### Post by darknuala on 2005-11-23
[QUOTE=ranf]Try Ctrl+R then type part of a command you typed before.[/QUOTE]

That is sweet.  And I thought I had a better way to do it!  That helps alot!
Thanks

---

