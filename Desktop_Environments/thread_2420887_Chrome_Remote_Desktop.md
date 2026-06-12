---
title: "Chrome Remote Desktop"
date: 2019-06-12
forum: Desktop Environments
---

### Post by Shibblet on 2019-06-12
I am having a hard time getting this to work. I go through all of the regular steps to setting it up, and it works for the most part...

The problem is when I try to remotely access my computer, all I get is a black screen with a small window that says "could not sync environment to dbus"

I'm not sure what that means, or how to fix it. My google search on this subject doesn't give me anything I can really understand... regarding a fix.

Is anyone aware of this issue, and hopefully, how to resolve it?

---

### Post by &amp;wP*!) on 2019-06-12
What is the operating system of your client (from which you get remote connection to the other machine) ?
What is the operating system of your server (to which you get remote connection) ?
What is the software version you are using to connect? 

Your post is fast to interpret. More technical details please, Alaska!

---

### Post by Shibblet on 2019-06-12
> **pencuse said:**
> What is the operating system of your client (from which you get remote connection to the other machine) ?
What is the operating system of your server (to which you get remote connection) ?
What is the software version you are using to connect? 

Your post is fast to interpret. More technical details please, Alaska!

The reason that I am using Google Remote Desktop, is that it works through a browser.  And the computer I want to use to access my home desktop, cannot have any additional software installed on it.  It has to work through a browser.  The client computer is a locked down Windows 10 computer, but does have Firefox, and it currently works with Windows 7 and 10 remote connections.

The home desktop is Kubuntu 19.04.

---

### Post by &amp;wP*!) on 2019-06-13
Ok, now we are one step ahead.
In your original message you wrote the message "could not sync environment to dbus" coming out.
dbus is a Linux feature - the message is coming from your Kubuntu desktop.

On server side: You should check the settings of your application on server (Kubuntu desktop), which are giving the service to the client (your computer with Windows 7/10). There is something wrong with the settings of your application in Kubuntu.  TCP port? Data rate? Color setting? IP address? It can be anything. 
On client side: Check your settings in Google Remote  Desktop. There is something which is not compatible to the application of Kubuntu.

These are my first guesses so far.

What is the name of this application on Kubuntu desktop? With that name, search the message "could not sync environment to dbus" in Google. You could find similar issues at other people.

---

### Post by Shibblet on 2019-06-13
> **pencuse said:**
> Ok, now we are one step ahead.
In your original message you wrote the message "could not sync environment to dbus" coming out.
dbus is a Linux feature - the message is coming from your Kubuntu desktop.

Yes.  When I log in from my remote computer.  The session shows a large black screen with a small window in the upper left hand corner that simply says "could not sync environment to dbus" and a small button below it that says "okay" but does not do anything when you click on it.

> **pencuse said:**
> On server side: You should check the settings of your application on server (Kubuntu desktop), which are giving the service to the client (your computer with Windows 7/10). There is something wrong with the settings of your application in Kubuntu.  TCP port? Data rate? Color setting? IP address? It can be anything. 
On client side: Check your settings in Google Remote  Desktop. There is something which is not compatible to the application of Kubuntu.

These are my first guesses so far.

Unfortunately there are not really any settings that can be made on Chrome Remote Desktop.  It was designed as a "download and run" application, and does all of the configurations for you.  When I use it on Windows 7 or 10 (server side) it works flawlessly with the Web Browser client.

> **pencuse said:**
> What is the name of this application on Kubuntu desktop? With that name, search the message "could not sync environment to dbus" in Google. You could find similar issues at other people.

To be honest, I don't really have to use Chrome Remote Desktop, I can use anything  that will work via a browser on the client side.  If there are any suggestions, I am game.

---

### Post by &amp;wP*!) on 2019-06-13
Then I propose to use an application other  than  Google Remote Desktop. That another application could be compatible to your setup in  Kubuntu desktop.
Unfortunately I have no more ideas.

---

