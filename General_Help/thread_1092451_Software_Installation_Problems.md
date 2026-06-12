---
title: "Software Installation Problems"
date: 2009-03-10
forum: General Help
---

### Post by jtan189 on 2009-03-10
This might be better off under the installation subgroup, but I think it's a general enough question.

I'm completely new to Ubuntu. I've messed around with it every once in while, but I've never seriously tried using it. I have my computer set up to dual-boot between Ubuntu and Vista, so I figured I would try to get to know it a little better. But to the question -

I was told by someone that it's better to install software manually, rather than by using the "Add/Remove" option or the Synaptic Package Manager. He said something about it ensuring you have the latest version directly from the source. Not sure if he's right or not, but I listened to him. I've tried installing two main programs on my computer, and neither of them are set up the way I want.

The first program is rtorrent. I followed this person's instructions, which had me using the terminal and typing in stuff which I had no idea meant. Anyways, I ended up putting the tarball (I think that's what they call compressed files here?) in the /usr/src/ folder. I'm not sure if that's where installations are supposed to go, but that's what I did. Then I unpacked it and compiled it and installed, using the ./configure, make, and make install commands. Had to install a bunch of other stuff with it, including some libtorrent thing. Anyways, I finally got it to work, but now I'm wondering if I put it in the right place. It seems wrong to install it into a folder which I can't even view without typing sudo (I'm not sure at all how to see what's inside it using Ubuntu's file explorer, whatever that is called). Plus, I don't think it would work to make a launcher for it, because of what I experienced with the second program.

Second program I tried also gave me troubles, and this one drove me near insane. I almost was going to give up on Ubuntu altogether (since I couldn't even install a simple program) until I settled down a bit and decided to come here. The program is Songbird. I didn't have specific instructions for installing this one, so I mimicked what I did for rtorrent. I got the tarball, used mv to move it from my Desktop to /usr/src/ and then unpacked it. Took me a while to figure out I needed to type ./songbird into the terminal instead of ./configure to install it. (as a side note, why can't I just double click something within the unpacked tarball to install it?) Once I had it installed, I wanted to make a launcher for it within my main Ubuntu menu. I googled around a bit and figured out that I should make it a menu item and use /usr/src/Songbird/songbird as the command (I hope that's right). But it wouldn't work because it wasn't allowed access to that folder or something. I looked around the internet and saw that people installed stuff into /opt/ also.

Here's a question: how do I uninstall a program if it doesn't show up in Add/Remove or the Synaptic (because I installed it manually)? I tried to uninstall Songbird because I was going to reinstall it into /opt/ by deleting the Songbird folder within /usr/src/, but I'm pretty sure that didn't work. When I moved the tarball to /opt/ and tried to reinstall it, it didn't go through the same thing and took half the time, like it was already installed. I'm not sure where things install to. So confused.

Anyways, so it was all useless anyways, because after moving it /opt/ I couldn't make my launcher anyways - same reason. Something about access restrictions. So the only way I can run Songbird is by opening a terminal, typing sudo -i, then my password, then navigating to /opt/Songbird/, and then typing ./songbird. That's not what I want. Is there some place installations should go?

Sorry this is a little long-winded, but I'm just so annoyed and confused and I have so many questions. I've got a bunch of Ubuntu/Linux guidebooks I'm going to read sometime, but with school and stuff right now, I just don't have the time to. I'd usually just say 'screw it' and stick with Vista, but I wanna figure out Ubuntu.

---

### Post by cariboo on 2009-03-10
I would suggest waiting until you are a little more experienced before installing programs from sources.

You can install rtorrent using Synaptic Package Manager and you can get the the .deb file for songbird [here]("http://www.getdeb.net/search.php?keywords=songbird").

The packages may not be bleeding edge, but they are a lot easier tro install.

To uninstall programs compiled from source, go into the source directory and type:

```
make uninstall
```

You would be much better off checking out the forums than listening  to someone that sounds like he is an elitist.

Jim

---

### Post by klemens on 2009-03-10
hmm a long story :p

First of all i just want to say this ain't the right way to start of with linux. What you're friend is telling you ain't a lie but still makes things really hard to start of.

Using the latest version of every program is great but not always necessary as long as the older version does what you need.

Apt-get and synaptic is what i call the power of ubuntu and debian and not using them would be kinda ... It handles all you're problems @ once. Next to that, all the software that you can install via synaptic are @ least tested in ubuntu to work, what ain't the case of all the software around.

So you're friend is probably a highly IT freak and knows what he does but using basic software as root ain't really a great idea.

As it comes to songbird it isn't in the repositrys, but you can find a .deb here [http://www.getdeb.net/app/Songbird]("http://www.getdeb.net/app/Songbird") once downloaded you can press 2 times on it to start the package installer like you're probably used in windows.

good luck with ubuntu ^^

---

### Post by klemes on 2009-03-10
For rtorrent you could just give :

```
sudo apt-get install rtorrent
```

in the console

which is the recommended way to install any program in any debian-based distribution like Ubuntu:
i.e. sudo apt-get install name_of_the_program_you_want_to_install.

For the second program I don't think it is listed in the repositories (you can easily see it for yourself by typing:apt-cache search songbird in the console)so if you need it you must install it manually,but remember to resort to such practises only if you absolutely need it ,this or any other program which is not comprised in the official repositories, because you can easily damage your installation.That's generally considered to be a good rule in any debian-based distribution.

---

### Post by jtan189 on 2009-03-10
> **cariboo907 said:**
> 

To uninstall programs compiled from source, go into the source directory and type:

```
make uninstall
```

Jim

Thanks for the tips. I guess I'll stick to Synaptic or apt-get for the time being. I think I was able to uninstall rtorrent with the "make uninstall" command, but when I tried it with Songbird, here's what I got:
> root@jtan189-laptop:/opt/Songbird# make uninstall
make: *** No rule to make target `uninstall'.  Stop.

Any idea how to fix this?

EDIT: Also, I just installed rtorrent using the apt-get command, but I don't know where it went. I see that I can launch it via terminal by typing "rtorrent", but I also want to make a launcher for it in the main menu.

EDIT2: I asked around the hub at my school and got some help. I guess I didn't install Songbird with ./songbird, but was in fact running it with that. And the way to uninstall it was to delete the directory for songbird in /opt. Also, I figured out that rtorrent was located at /usr/bin/rtorrent, so I made a launcher ("launch in terminal") with that location as its command. Seems to work alright. So if I did any of this wrong, feel free to correct me. And thanks to everyone for their help. I'm sure I'll be back soon.

---

