---
title: "remote to beryl"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by sqela on 2007-04-26
currently im using fawn on my home box and i would use vnc viewer to remote into it. however after sucessfuly installing beryl. i am able to log on and view but not do anything else on the box im remoting into. any other session it works fine i.e. metacy etc etc

my question is how do i leave ubuntu in beryl and still be able to log into my box?

---

### Post by Jonne on 2007-04-26
Maybe by using ssh? Install the ssh server first, then:

from a Linux box, use 'ssh -x <your box>', when you type the name of your app 'firefox', or 'nautilus --no-desktop'. Your app will run on your desktop, while it still runs on your remote machine. It's also faster than vnc, and more secure.

From a Windows box, you need to install and run an x-server first (Try Xming, but there are others), and Putty. Start putty and enable X11 forwarding (either by using the checkbox, or by adding an -x switch when you start it).

---

### Post by sqela on 2007-04-27
xming won't work with my win98 box any others that are good that work with 98?

---

### Post by Jonne on 2007-04-27
Hmm, there are some others you could try (there's a list [here](http://en.wikipedia.org/wiki/X-server#Implementations)), but if that doesn't work out i can't help you with your vnc issue...

---

### Post by sqela on 2007-04-27
just tried tight vnc the screen comes up but only the mouse moves and thats it but atleast its progress withultravnc the screen was somewhat disorted

still cant get it to work

---

### Post by sqela on 2007-04-27
think im on to something. using tight vnc i log in and i think its working but relly slow. for example i click the firefox icon on my desktop but nothing happens. i shut down vnc and reatempt it to find the browser has opened. i try moving the window and nothing happens yet next time i log in i find the wondow has moved. so im guessing it works but relly slow now how do i speed it up?

---

### Post by synthaxx on 2007-04-27
I've had similar problems, so maybe i can help you out.

First, try installing CYGWIN/X using [this]("http://x.cygwin.com/") link.
When you've installed it, run it to get a bash prompt. From here run "X -multiwindow &", this will start the X server.
Now make a connection to your linux box with ssh, be sure you use the -X parameter (your command line should look like this: "ssh -X yourusername@yourboxip").

Time to move to your linux box.

Now i don't remember exactly how i did it, so i'll just give you my current setting. Go to System > Administration > Login Window, and on the remote tab set it to something other then "Remote login disabled" .  Now on the "Security" tab disable the "Deny TCP connections" option to allow you to run it remotely.

Phew! We're not done yet but luckily these things are a one time only.

Go back to your windows/CYGWIN box. You should allready be able to start Windowed programs (try running "firefox-bin &"), but no login/desktop yet. To get this run "sudo apt-get install Xnest" and wait for it to finish.
Now for the magic, Xnest allows you to run a second X session in a window, and the X server on your local machine can receive the X window instructions and display them locally. This means that by running the following command on your remote X session: "Xnest :1 -query localhost -geometry 1024x768" you get the login window of the remote machine, and you can start a second X session.

I could have forgotten some steps, i didn't really have time to retrace everything, so if anyone sees anything missing please jump in. After these steps you can streamline it all you want (have cygwin start the server and login automagically for example).

Also remember that the X session you started is not persistent. If you close the window everything contained within it is lost. I havent really been able to find anything to get around that.

---

