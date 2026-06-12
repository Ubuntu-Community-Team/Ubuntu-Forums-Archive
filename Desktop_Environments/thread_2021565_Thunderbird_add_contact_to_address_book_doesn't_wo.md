---
title: "Thunderbird: add contact to address book doesn't work."
date: 2012-07-09
forum: Desktop Environments
---

### Post by crixtiano on 2012-07-09
**Version:**
Ubuntu 12.04
Thunderbird 13.01

**Problem:**
When trying to add a contact, I click the "OK" button, but the contact is not inserted, or even the window is closed.

See the screenshot: [http://postimage.org/image/d2lxlgq0j/](http://postimage.org/image/d2lxlgq0j/)

Someone confirm this bug? Do you have any solution?

Thank you.

Cristiano

---

### Post by Rex Bouwense on 2012-07-09
Did this problem just start?  I too am using Thunderbird 13.0.1 without incident.  Try closing the window and starting again.

---

### Post by crixtiano on 2012-07-09
> **Rex Bouwense said:**
> Did this problem just start?  I too am using Thunderbird 13.0.1 without incident.  Try closing the window and starting again.

:-)

I closed and opened the program several times and the error persists.

---

### Post by Rex Bouwense on 2012-07-09
Just checked launch pad and the only bug reported dealt with Thunderbird 13.0.1 installed on Kubuntu 11.10.  At least that was the only one that I found.  Did this just start?  Can you make changes to contacts that you already have in your address book?

---

### Post by crixtiano on 2012-07-09
> **Rex Bouwense said:**
> Just checked launch pad and the only bug reported dealt with Thunderbird 13.0.1 installed on Kubuntu 11.10.  At least that was the only one that I found.  Did this just start?  Can you make changes to contacts that you already have in your address book?


No! I can not edit anything, because the "OK" button does not work. By clicking "OK" nothing happens, the window doesn't close and nothing is edited.

I started using Thunderbird yesterday and I see this error today when trying to insert a new contact.

:(

---

### Post by circlemaster on 2012-07-09
Maybe you can try to write **thunderbird** in a terminal and see if you get any error messages.

---

### Post by crixtiano on 2012-07-09
> **circlemaster said:**
> Maybe you can try to write **thunderbird** in a terminal and see if you get any error messages.


I've tried to do this. By clicking "Ok" nothing appears on the terminal.

:(

---

### Post by ajgreeny on 2012-07-09
> **crixtiano said:**
> I've tried to do this. By clicking "Ok" nothing appears on the terminal.

:(
???
This comment does not make sense!

Circlemaster meant for you to open gnome-terminal and type **thunderbird**  then hit enter to see if any error messages appear in the terminal when TB crashes.

Are you still using Feisty Fawn 7.04, as your info says, or is it still saying that because you haven't changed it?  If you are, that could account for your problem.

---

### Post by crixtiano on 2012-07-09
> **ajgreeny said:**
> ???
This comment does not make sense!

Circlemaster meant for you to open gnome-terminal and type **thunderbird**  then hit enter to see if any error messages appear in the terminal when TB crashes.

Are you still using Feisty Fawn 7.04, as your info says, or is it still saying that because you haven't changed it?  If you are, that could account for your problem.



> $ thunderbird
Error: No such tab mode: chat
-- Exception object --
+ fileName (string) 'chrome://messenger/content/tabmail.xml'
+ lineNumber (number) 465
*
-- Stack Trace --
openTab("chat",[object Object])@chrome://messenger/content/tabmail.xml:465
get_selected()@chrome://messenger/content/chat/imconv.xml:121
()@chrome://global/content/bindings/richlistbox.xml:576


**Note: **The above error occurs when closing Thunderbird.

---

### Post by ajgreeny on 2012-07-09
Looks like a problem in your profile, but I am not totally sure.

I have looked for a file called **tabmail.xml** which your system seems to complain about but I do not have any file of that name, so I can't really help further.

---

### Post by crixtiano on 2012-07-09
> **ajgreeny said:**
> Looks like a problem in your profile, but I am not totally sure.

I have looked for a file called **tabmail.xml** which your system seems to complain about but I do not have any file of that name, so I can't really help further.


I renamed the user folder and started Thunderbird again:

$ mv .thunderbid thunderbird_BKP
$ thunderbird

The error remains. I can not add any contacts.

:(

---

### Post by Rex Bouwense on 2012-07-09
You always have the option to completely uninstall Thunderbird and then re-install.

---

### Post by crixtiano on 2012-07-09
> **Rex Bouwense said:**
> You always have the option to completely uninstall Thunderbird and then re-install.

After these commands:

> $ sudo aptitude update
$ sudo aptitude safe-upgrade -y
$ mv .thunderbird thunderbird_BKP
$ sudo aptitude reinstall thunderbird

Nothing happens. I still can not add any contacts in my address book.

---

