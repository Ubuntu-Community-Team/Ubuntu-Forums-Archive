---
title: "How to change what the password screen displays"
date: 2009-04-05
forum: General Help
---

### Post by mlissner on 2009-04-05
I was thinking about the scenarios that might happen if my laptop is stolen, and I realized that if it is stolen when it is suspended, when the laptop is turned on, it will show the password screen with both my full name and username.

Is there anyway to edit the password screen that comes up when ubuntu resumes from suspend, or from being locked? I would love to be able to edit what is displayed.

I should note that I'm NOT referring to the login screen.

---

### Post by lisati on 2009-04-05
I was about to suggest changing the login window. Do you mean the user switcher on the top panel?

---

### Post by blackened on 2009-04-05
He means the one that shows up when you resume from suspend. It's the same as comes up when you return from locking the desktop.

---

### Post by mlissner on 2009-04-05
> **blackened said:**
> He means the one that shows up when you resume from suspend. It's the same as comes up when you return from locking the desktop.

Yep. Nobody knows, huh?

---

### Post by blackened on 2009-04-05
> **mlissner said:**
> Yep. Nobody knows, huh?

Sorry, was dog tired last time I responded and didn't have time to track down what you were asking for.

Ok, this will require the editing of the lock-dialog-default.glade file in /usr/share/gnome-screensaver. ***Make a backup first, just in case.***

```
sudo gedit /usr/share/gnome-screensaver/lock-dialog-default.glade
```

[COLOR="Red"]1.[/COLOR] To hide your real name, start by finding these lines (line numbers 78, 79, and 80):

```
<widget class="GtkLabel" id="auth-realname-label">
			  <property name="visible">True</property>
			  <property name="label" translatable="yes">**&lt;span size=&quot;x-large&quot;&gt;%R&lt;/span&gt;**</property>
```

Now you would think that simply setting the "visible" property to "False" would fix this, but it just ain't so. Instead you have to delete all the nested HTML info (the bolded stuff), including the %R variable that links to your real name.

The result should now look like this:

```
<widget class="GtkLabel" id="auth-realname-label">
			  <property name="visible">True</property>
			  <property name="label" translatable="yes"></property>
```

[COLOR="Red"]2.[/COLOR] To hide your username and/or hostname find these three lines (line numbers 103, 104, and 105):

```
<widget class="GtkLabel" id="auth-username-label">
			  <property name="visible">True</property>
			  <property name="label" translatable="yes">&lt;span size=&quot;small&quot;&gt;**%U on %h**&lt;/span&gt;</property>
```

Same idea applies, except here you can just delete the content nested in the HTML tags. Where it says "%U on %h", %U is your username and %h is the hostname, so deleting the proper one, or both, should have the desired effect. In this case, you can leave the HTML tags and only delete the content.

If you choose to delete your username but leave the hostname intact, the result should look like this:

```
<widget class="GtkLabel" id="auth-username-label">
			  <property name="visible">True</property>
			  <property name="label" translatable="yes">&lt;span size=&quot;small&quot;&gt;%h&lt;/span&gt;</property>
```

Since this is just nested HTML, you can do pretty much whatever you want with it. If you botch it, then you may have to kill the xserver to get back to GDM so you can restore the backup. Just so you're aware.

---

### Post by mlissner on 2009-04-05
Wow. This worked beautifully. It looked very strange without anything in either of those fields, but I left the first one saying "Welcome," and now it looks normal, and preserves my privacy. 

Perfect, thanks!

---

### Post by mlissner on 2009-04-05
Actually, not quite perfect - I noticed that if you click the "leave message" button, it still tells you who the logged in user is. So, I changed that too by editing line 418 or so of the same file.

---

### Post by Bios Element on 2009-04-05
Just a little note...If it 'is' stolen, How the heck will someone know who to give it back too without a name? And even if a thief got a real name/username, Who cares? It's not like it'd be any use to them.

---

### Post by mlissner on 2009-04-05
Well, the idea is that if it's stolen, at least they know nothing about me, and don't have any of my information. I use drive-level encryption too, so unless they're pretty sophisticated, my laptop is pretty much untouchable. 

I'm a bit pessimistic about ever getting a stolen laptop back, but I do have bits and pieces of identifying information about the computer such as the serial number and mac address that I can give authorities on the off chance they do get my laptop back.

---

### Post by blackened on 2009-04-05
Getting more than a little off-topic. Maybe starting a new thread about best practices in case of theft would be prudent.

---

