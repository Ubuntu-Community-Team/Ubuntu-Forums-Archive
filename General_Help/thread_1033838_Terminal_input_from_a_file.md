---
title: "Terminal input from a file?"
date: 2009-01-07
forum: General Help
---

### Post by jrounds on 2009-01-07
Hi.  I am trying to write a gedit script to help me work with R.

And I don't want to reinvent the wheel.  So let me ask you this.

So gnome-terminal takes input from the user. And you can launch a program like R that is a text based program in it.  The gnome-terminal is still running and handling input, and the R program is running and getting input from gnome-terminal.

My question is this:

Is there a terminal program that will do that but let you specify a file or somehow a pipe such that anything that comes from it will be considered input while also the keyboard and all that works as normal?

See I can pipe the stdin, but thats not what I want because then all the input comes from the stdin pipe.  Now this could be written, and in fact I have seen a console apt specific to python interpreting that did this.  But all want is something general that will run a shell and take alternative input from something that launched it via file (or some sort of pipe).

Anything like that out there.  Something like gnome-terminal that can stdin as normal, but also stdin from a file?

---

### Post by croto on 2009-01-07
Hi, my friend. I really like your question, and I wish I knew the "right" way to do it. The only way it occurs to me how to solve your problem is a kind of dirty hack, but if you're interested, let me try to explain it. 

I'd use a combination of two utilities: screen and socat. Probably screen is installed by default with ubuntu, but you'll have to install socat yourself. You may know these programs: screen is a terminal multiplexer, it lets you do cool things like attaching and detaching from terminal sessions. If you don't know the command, it will blow your mind. Just read any tutorial on it. 
The socat utility is more complex. It's like netcat for any kind of sockets. I'm not going to get into details, but it's a VERY interesting program.

If you're still with me, I'd recommend that at least you have a good idea of how to use "screen", so before continuing with this, play a while with it: create a few sessions, attach to them, deattach, feel familiar with it. It's very easy.

Now that you're the "screen" master, my idea is the based on the fact that screen allows you to have two or more people connected to the same session: everybody could see the screen, and what everybody types goes to the session (play a little bit with "screen -x" instead of "screen -r": create one session, and attach from several terminals using screen -x). The idea is, what if instead of another user attaching with "screen -x", I pipe a file into the screen session? Hmm, sounds good! The problem is that a simple "cat file | screen -x" would not work because screen will complain since it expects a "real terminal" to connect, not just a file.

This is where socat comes in. It can take the file and connect it to screen via a "fake terminal". Example. Suppose you have a screen session running where you're happily doing your statistics, and you want to pipe the file "myfile.txt" into the session. What you can do is:
```

cat myfile.txt | socat - EXEC:'screen -x',pty,setsid,ctty > /dev/null

```
That's it! At least, it worked on my machine, I hope it works on yours too.

Happy hacking! If you find a cleaner solution, let me know!

---

### Post by dougpan on 2009-01-07
Have you considered a pipe from the tail program?

For instance: tail -f $YOUR_FILE | while read -p line

Doug

---

