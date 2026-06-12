---
title: "Dash can't find Epiphany web browser"
date: 2012-01-25
forum: Desktop Environments
---

### Post by quadrantids on 2012-01-25
I have downloaded Epiphany web browser using the Ubuntu Software Centre but Dash cannot find it.

The only way I have managed to find it is using Synapse, which, I have to say, I find produces more relevant results and faster.

Since Dash cannot find my Epiphany browser to launch, does Ubuntu 11.10 have an applications hierarchy where I can choose an application to launch from a list?

I find this really frustrating!

Thanks in advance

---

### Post by Frogs Hair on 2012-01-25
Sometimes if an application hasn't been opened yet it will not appear when typing a keyword . Open dash , select Internet Apps , select installed ,  open the  browser and save the icon int he launcher if you want .

Once the application has been open it  usually appears when typing a key word . If you have done this then I don't know what the problem may be . I have had to do this with two applications .

---

### Post by gordintoronto on 2012-01-25
Using Ubuntu 11.10, I ran Software Center. I told it to install Epiphany. Is that also true for you?

I clicked on the Dash, typed "epi" and Ephiphany's icon appeared.

I clicked on the Dash, clicked on "Internet Apps," Epiphany was one of them.

I don't know what Synapse is. Perhaps you could tell me?

---

### Post by quadrantids on 2012-01-28
I am using 11.10 and have recently installed Epiphany browser to try out. It simply doesn't show up in Dash so I had to install Synapse which finds it  without any problem. (Incidentally Synapse seems to be faster and provide more pertinent results overall compared to Dash)

When Dash can't find an app, is there no hierarchichal tree in 11.10 that enables me to see what apps are installed and where so that by clicking on it in the old-fashioned way I can at least get it to run?

Perhaps the only alternative is the command line?

Thanks for any help anyone can provide.

---

### Post by MG&amp;TL on 2012-01-28
Hierarchical structure? No.

Okay, a simple fix is to make an entry yourself. :)

Make a new file, called epiphany.desktop, in your home folder.
Add the following content:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=Epiphany
Comment=Browse the web
TryExec=/usr/bin/epiphany
Exec=/usr/bin/epiphany
Icon=web-browser

```

Then run the following command in the terminal:

```
sudo cp epiphany.desktop /usr/share/applications
```

You may need to log out and in again for this to take effect.

Hope this helps.

PS youcan delete the file in your homefolder once you're done.

---

### Post by lisati on 2012-01-28
Threads merged. One thread per problem please.

---

### Post by quadrantids on 2012-02-21
It's a keyboard launcher that seems to work better than Dash every time. You can get it from the Ubuntu software centre.

---

