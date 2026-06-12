---
title: "NX Web Companion Installation"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Jaygo333 on 2006-02-17
Has anybody heard of NX Web Companion. 
A java based NX taht runs in your browser. 
I just found it and trying very hard to install and having problems.
If naybody has it installed, how did you do it?

:h34r: Jaygo333 :h34r:

---

### Post by Jaygo333 on 2006-02-17
Has anybody heard of NX Web Companion?

Its a java based program that allows you to connect to you FreeNX server and control it throught the web. 
I just found it and is haveing trouble installing it. 
I'm trying to install from: [http://www.nomachine.com/documents/plugin/install.html#2](http://www.nomachine.com/documents/plugin/install.html#2)
 and having trouble ubderstanding the whole bit about installing ti in Ubuntu(.deb)
Could somebody please put it in simple layman language for me?
Also, if anybody else has managed to install it, please teach how you di it.

:h34r: Jaygo333 :h34r:

---

### Post by Jaygo333 on 2006-02-20
Somebody help here.
I'm tired of installing NX Client for windows everywhere I go to access my machine.
Is there an option like vncviewer.
Something standalone.

:h34r: Jaygo333 :h34r:

---

### Post by rrolfe on 2007-12-27
1. download the .deb file and double click it
2. read the documents that came with the app, it tells you where to get all the plugin files.
3. copy the files to the root fo your webserver ( usually \var\www , you will need apache2 or similar installed)
4. you need to alter the html and tell it the name of the server your using and some other details.
5. next the vital thing is you need to copy a cofig file .nxs to the sessions folder on the webserver, this will be in the same folder as the plug in.
6. to make the session file open a connection to the server you got your NX server running on and save it. it should show up in your home folder in the folder .nx ( turn on hidden folders)

i on the ohter hand have not been able to get freenx server working i can onyl get the nomachine nx server, only one connection, any pointers ?

also i think you might need a session file per user using the web connection.

more details instructions of what to change here:
[http://www.nomachine.com/documents/plugin/install.html](http://www.nomachine.com/documents/plugin/install.html)

if you get the java applet frezzing or doing nothing, you need a session file or to alter the hmtl page.

---

