---
title: "How To - Integrating Gmail into the Ubuntu Environment"
date: 2009-01-12
forum: Desktop Environments
---

### Post by ernz on 2009-01-12
Hi everyone! Another how-to describing the steps I undertook to resolve a small feature enhancement I have been looking at for a while. The steps below should integrate the Gmail e-mail web application fairly seamlessly into your Ubuntu Desktop. Note that the instructions below were put together for Ubuntu 8.10 - Intrepid Ibex and I was using Firefox 3.0 Version 3.0.5.

[SIZE="4"]**Step 1: Handling Mailto's**[/SIZE]
Mailto links within browsers are handled bu Evolution by default. We can set up Firefox to respond to a mailto click by opening a compose windows directly in Gmail.

**1)** Open up your [Gmail]("http://www.gmail.com") in Firefox and log in.
**2)** Copy and paste the following link into the address bar:
```
javascript:window.navigator.registerProtocolHandler("mailto","https://mail.google.com/mail/?extsrc=mailto&url=%s","GMail")
```
**3)** You'll see prompt at the top of the page to add the application. Accept.

[IMG]http://img240.imageshack.us/img240/7216/mailtohandlerow4.png[/IMG]

**4)** In Firefox > Edit > Preferences > Applications > Search for "Mailto" Content Type > Make the action "Use GMail". Done

I also recommend installing the AdBlock Plus and Better Gmail 2 Firefox Addons for a better Gmail experience. They can be found...
[http://adblockplus.org/en/]("http://adblockplus.org/en/")
and
[https://addons.mozilla.org/en-US/firefox/addon/6076]("https://addons.mozilla.org/en-US/firefox/addon/6076")
...respectively.

[SIZE="4"]**Step 2: Preferred Application - GMail!**[/SIZE]
Because GMail is not a client-side web application, we need to put in place a couple of workarounds to point Ubuntu towards GMail WITHIN Firefox rather instead of just a Gmail application like [Mozilla Prism]("http://blog.wired.com/monkeybites/2007/10/mozilla-prism-r.html"). I prefer this method because it feels less intrusive, and means that your E-mail and web browsing are still in a single Firefox session which, to me, feels more natural. While both are good solutions, this is by far the more "seamless".

**1)** Open a terminal session. (Applications > Accessories > Terminal)
**2)** Enter 
```
mkdir ~/.scripts
```
**3)** Now enter 
```
gedit ~/.scripts/open_mailto.sh
```
**4)** In this new text file paste the following
```
#!/bin/sh
firefox "https://mail.google.com/mail?view=cm&tf=0&ui=1&to="`echo $1|sed -e 's/?subject=/\&su=/' -e 's/mailto://'`
```
... and close gedit and return to the terminal.

**5)** Set the script as executable with the following terminal line
```
chmod +x ~/.scripts/open_mailto.sh
```
... and Close the terminal.

**6)** Open System > Preferences > Preferred Applications > Internet > Mail Reader
**7)** Use a 'Custom' application, and in the box below enter
```
sh /home/YOURUSERNAME/.scripts/open_mailto.sh %s
```
...obviously replacing YOURUSERNAME with your actual user login name.

[IMG]http://img397.imageshack.us/img397/7271/preferredgq1.png[/IMG]

Your default e-mail application according to Ubuntu, is a Gmail compose window which will create a new e-mail with auto-populated 'To:' field for any client-side E-mail links.

**[SIZE="4"]Step 3: Address Book[/SIZE]**

There are quite a few Gnome tools such as the contacts applet on the panel which depend on the Evolution contacts list to look up people and send contacts. With an application called 'Contacts' you are able to manually amass your Evolution contacts without using Evolution as a Mail client. 

**1)** System > Administration > Synaptic Package Manager > Settings > Repositories > Third-Party Software > Add button (Bottom left) and add this:```

deb http://debian.o-hand.com hardy/
```
**2)** Reload

**3)** Search for "contacts" and install - It will have an entry in the Office submenu.

**[SIZE="4"]Step 4: Contacts Lookup[/SIZE]**

Now that we have have system and browser mailto handlers, and somewhere to store the contacts, you can now add the applet to quickly lookup the contacts from your address book.

Right Click a Panel > Add to Panel > Double-Click "Address Book Search".

[IMG]http://img80.imageshack.us/img80/3259/contactsaf6.png[/IMG]

You can now quickly find contacts, click on them and send mails to them within Gmail compose.

**[SIZE="4"]Step 5: Notifier[/SIZE]**

The last step is to install checkgmail to notify you when a new e-mail lands in the Inbox. The same application can be used to quickly compose a new mail (right click the tray icon).

**1)** To install, go back to the terminal and type
```
sudo apt-get install checkgmail
```
**2)** Press ALT+F2 and type
```
checkgmail
```
...to start the application.

**3)** Right click the new Gmail icon and configure to use your own login details.

**4)** Add to Ubuntu start up. Systems > Preferences > Sessions > Add. Use whatever name you like, but the command must be "checkgmail" (without the quotes).

That's everything! You should now have effortless Gmail access and good integration on Ubuntu 8.10.


[I]Thanks to the authors of the original articles where I sourced the methods used above:
[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/")
[http://lifehacker.com/392287/set-firefox-3-to-launch-gmail-for-mailto-links]("http://lifehacker.com/392287/set-firefox-3-to-launch-gmail-for-mailto-links")
[http://www.pimlico-project.org/contacts.html]("http://www.pimlico-project.org/contacts.html")

Big thanks also to simplenewb for repo help and to Hikeractive for his input on mailto support.[/I]

---

### Post by topjohn on 2009-01-22
great how to!  i currently use prism for checking gmail.  is there anyway to write this so prism comes up?

---

### Post by ernz on 2009-01-26
Hi topjohn. I tried using prism but the contacts applet compose launcher would not work properly. If you do find a way of making it work, please drop a message back here to let everyone else know. Thanks!

---

### Post by Turtle.net on 2009-06-19
Great Howto, and it integrates perfectly with Gnome-Do Gmail plugin.
Now when I type a contact name, Do can send directly a message via gmail.
Just amazing :)

---

### Post by tylerisfat on 2009-08-23
> **ernz said:**
> Hi topjohn. I tried using prism but the contacts applet compose launcher would not work properly. If you do find a way of making it work, please drop a message back here to let everyone else know. Thanks!

How the heck can i get my gmail to look like yours?

---

### Post by ghostborg on 2009-10-05
Choose "compose in full Gmail" to make it show everything.
Change this in Google Gmail settings to make default.

---

### Post by aresazi on 2010-01-25
Good post ernz

You can however shorten your step 1 & 2 dramatically:

1)Open System > Preferences > Preferred Applications > Internet > Mail Reader
2) Use a 'Custom' application, and in the box below enter
```
xdg-open https://mail.google.com/mail/?extsrc=mailto&url=%s
```

That's it! mailto links will now open in your default browser anywhere you click them.

---

### Post by nilarimogard on 2010-01-25
There is a package which does all that with a double click (.deb package): [Gnome Gmail]("http://www.webupd8.org/2009/09/gnome-gmail-allows-gmail-to-be-selected.html").

---

### Post by OrangeCrate on 2010-01-25
If you use Firefox to check your email, you can also just change the default to Gmail, by doing the following:

Edit > Preferences > Applications > mail to, and change the default from "use Evolution, to "Use Gmail".

---

### Post by BFG on 2011-03-26
This is great.  Does anyone have an idea how to get the script to open Chromium?

```
google-chrome "https://mail.google.com/mail?view=cm&tf=0&ui=1&to="`echo $1|sed -e 's/?subject=/\&su=/' -e 's/mailto://'`
```

Doesn't work


Edit - found an answer here:
[http://stackoverflow.com/questions/4887753/mailto-open-google-chrome-in-ubuntu-with-notify-msg](http://stackoverflow.com/questions/4887753/mailto-open-google-chrome-in-ubuntu-with-notify-msg)

For chrome, the script needs to contain.....

```
str=$(echo $1|sed 's/.*mailto:\([^?]*\)?.*/\1/')
google-chrome -app="https://mail.google.com/mail/?extsrc=mailto&url=`echo $1`"
```


Works with the subject line too.

---

