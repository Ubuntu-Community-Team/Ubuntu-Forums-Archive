---
title: "Modem Dial on Button Press"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Elitist_Phoenix on 2005-10-19
I'm wondering is there anyway that I can get my (serial) modem to dial with a button press. (Bit of background) The box acts as a internet gateway for the other computers on the lan, and also as my private linux desktop. This is why I need a button press that will work anywhere anytime (even if xlock is going) and not like (gnome lights or whatever). Its just so when I'm not there my box can dial for my family so they can use the internet to. Thanks in advance.

---

### Post by HermanAB on 2005-10-19
Howdy,

Actually, you don't even need a button press!  

Using diald, you can set the system up to automatically dial up as soon as an application wants to go online and hang up after a period of inactivity.

Do some googling for diald howtos.  Years ago, I used a guide by Egil Kvaleberg, but I haven't used diald since DSL took off.  You should be able to get it going just with the man page, since it is quite simple.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by migueljacq on 2005-10-19
I think if you add the modem applet to your panel, a right click on it includes an activate/deactivate option.

---

### Post by Elitist_Phoenix on 2005-10-19
Thanks guys thought about these already.
1. Modem Applet won't work because I lock the screen when I go out.
2. The diald is an okay idea, but as soon as any app tries to access internet from any of the computer (e.g. M$'s E.T phone home) this will dial when its not needed. For example I want to have a single player game of CS Source, that (f**king steam s**t) will try to access the internet and make the modem dial.
Though thanks for the replies anyway.

---

### Post by migueljacq on 2005-10-19
If the idea is to let other members of your family use the box to get on the internet, is there a common time this will happen? Coz I was thinking maybe write a crontab that automatically connects to the net at given intervals automatically.
My old man runs a cron that connects to the net at certain times, writes the IP number to a file and then sendmail emails it to him at work so he can hack his own machine when he gets bored :-)

---

### Post by Elitist_Phoenix on 2005-10-19
Good thought and lol (hack machine). However its just random chaos (no specified times) here and we've only got one phone line so they will disconnect it when they need to use the phone. Though thanks for the continued help. What I think I need is a small script that executes through "init.d" and stays resident, just detecting a certain key code and executing a command (e.g. ppp-go).

---

### Post by migueljacq on 2005-10-19
[QUOTE=Elitist_Phoenix]Good thought and lol (hack machine). However its just random chaos (no specified times) here and we've only got one phone line so they will disconnect it when they need to use the phone. Though thanks for the continued help. What I think I need is a small script that executes through "init.d" and stays resident, just detecting a certain key code and executing a command (e.g. ppp-go).[/QUOTE]

Well it's easy to write aliases like that, not sure about how you want it to do automatically, or do you want the family members to be executing 'ppp-go'

---

