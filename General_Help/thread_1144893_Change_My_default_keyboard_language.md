---
title: "Change My default keyboard language"
date: 2009-05-01
forum: General Help
---

### Post by xxmp on 2009-05-01
Hello all i change my default keyboar language to greek and now when i open ubuntu i had to write username.pass in english ;/ how can i change the input language to english again to log in in ubuntu thank you very much

---

### Post by delcypher on 2009-05-01
There are two ways

1. Change the input language at the login screen.

Click "Options > Select language" then choose your language

This can also be done by pressing [ALT]+t then press l, then choose your language

2. This way isn't so good but it works.

Press  [CTRL]+[ALT]+[F1] , a terminal should appear (if it doesn't press the key combination again)

login as yourself (i.e. type in your username, press enter, type in your password, press enter)

now type.```
sudo /etc/init.d/gdm stop
```

This will stop X-server from running. Now type
```
startx
```

This should start X-server and should already be logged in (somethings won't work correctly though), change the language settings and then logout. 

If you can't do this then reboot by typing```
sudo reboot
```.

This is a much uglier way to do it. The first method is preferable and should work.

---

### Post by xxmp on 2009-05-01
the problem is that with the first way i still write greek although i change to english uk and with the second way i see a terminal but again i write greek and i can not log in:S .Do you know any other way to change to english to log in?Thank you very much for you help .The problem is that my username and pass is in english and i only write greek so i con not log in :S Is there any way like shift+ctrl in windows to change language in ubuntu?

---

### Post by delcypher on 2009-05-01
I don't quite understand you. What do you mean by "I still write greek". In the proper terminals I was under the impression that you can only type in English no matter what your language is set to in X.

---

### Post by xxmp on 2009-05-01
in the terminal I write again greek. Is there any way to log in in a safe mode and change the language?

---

### Post by delcypher on 2009-05-01
You could try going into recovery mode (select (recoverymode) at bootup (GRUB SCREEN) - you may have to press [ESC] to get to it.

Then select "Drop to root shell prompt" (it might be called something slightly different"

You could then try:

1. Edit /etc/enviroment and add the line ```
LANG="en_US.UTF-8"
```.  You can use vi or nano (easier to new users) to edit the file. Then restart and see if this works.

2. Edit /etc/gdm/gdm.conf-custom under [greeter] add the line ```
Language=en_US.UTF-8
```. Restart and try to login again

I'm sure there are better ways of doing this, but these are the only ways I know.

---

### Post by coniliakis on 2009-05-03
(&#931;&#964;&#959; &#947;&#961;&#940;&#966;&#969; &#945;&#947;&#947;&#955;&#953;&#954;&#940; &#956;&#953;&#945;&#962; &#954;&#945;&#953; &#949;&#943;&#957;&#945;&#953; &#964;&#959; forum &#945;&#947;&#947;&#955;&#953;&#954;&#940;:))

I installed Ubuntu 9.04 in English and chose Greek simple keyboard layout. However, when I open an application or terminal, the default input language is Greek. What I did is going to System-> Preferences -> Keyboard, clicked on Layouts tab clicked on USA, set it as Default if it isn't allready and clicked on Apply System-wide and Close.

After that, any new terminal window, or application gets English as default input language, when start typing.

&#915;&#949;&#953;&#945; &#963;&#959;&#965; &#960;&#945;&#964;&#961;&#943;&#948;&#945;.

---

