---
title: "Setting Up Multiple Login Sesisons"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by janascii on 2007-05-16
I've been trying to figure out how to set up multiple sessions in form the login screen.  Basically what I want is two sessions that will have different configurations.  In my case one running metacity that will allow me to use a TV I have hooked up, and one that uses beryl when I'm only using my monitor.  Is there any way to do this?

---

### Post by jkwarras on 2007-05-16
Do you mean two independent sessions, one will launch on TV and other on monitor? It could be done, but if you want really independen sessions, I mean working on a session while watchign TV on the other, it's really difficult. If you have two video cards it should be possible, just google for it. If you have only one card, and you connect via S-Video, then I doubt you can achieve it as when you are i.e. on the monitor session, the TV output will switch to this one, even if you're disable it for this session and viceversa, if you're on the TV session, you'll not have input on the monitor.

I'm also looking for that, but I didn't find an answer, the closest thing I foudn ont he net, but I din't succed, it's this tutorial using something called Xephyr: [http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

---

### Post by janascii on 2007-05-22
That might also work but what I was talking about was under the sessions menu on the gdm login page.  Having two gnome options with different configurations.

---

### Post by seamus7 on 2007-06-04
I too am trying to create multiple sessions (startup groups) so that I have a choice upon login to GDM. One session named Multi-media might startup Amarok, Azureus and GIMP while another session named Blogging might startup Gftp, Firefox and Gedit. That's the idea. But alas there seems to be a problem for when I go to Help in the Sessions window I'm told that upon log out I ought to be presented with a screen offering to create and name a new session but it doesn't appear. Is this feature just not well implemented yet??? Buggy???? Anyone?

---

### Post by jkwarras on 2007-06-07
> **janascii said:**
> That might also work but what I was talking about was under the sessions menu on the gdm login page.  Having two gnome options with different configurations.
It can be done, but I don't know exactly how.

---

### Post by eentonig on 2007-06-07
I have it running like that. I have a seperate session that's starts Beryl and another with plain old Gnome. 

I used a Howto from the Beryl website to create the Beryl GDM session entry.

---

### Post by Sweet Mercury on 2007-06-14
> **eentonig said:**
> I have it running like that. I have a seperate session that's starts Beryl and another with plain old Gnome. 

I used a Howto from the Beryl website to create the Beryl GDM session entry.

Yeah, I'm seeing a few HowTos like that myself.

This is definitely something that shouldn't be as difficult as it seems, considering there is a sessions manager built in to the UI.

edit: The "Yelp" desktop help, when I push the *Help* button in the Session manager, says that under the "Sessions" tab (which isn't there), should have an "Add" session button which should allow users to Add a new session.

I tried launching the session manager as root to see if that option would be available, but I couldn't do that.

---

### Post by ncappel1 on 2007-06-16
I thought that I would put a link to another thread that is discussing this same topic.
[http://ubuntuforums.org/showthread.php?p=2859114](http://ubuntuforums.org/showthread.php?p=2859114)

---

### Post by andersja on 2008-05-13
janascii: loads of links and an opportunity to vote here:

[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

