---
title: "Talk to me about window decorations..."
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by fogster on 2007-07-27
I'm a brand-new convert to Compiz Fusion and XGL. I've used the guide here to do it, and mucked around a bit. Basically, I'm wondering if anyone can either link me to a good description of window decorator options, or explain it to me...

In my startxgl.sh, I start gnome-session, since I was having bizarre problems like my shut down button not showing up. So even after running compiz --replace from within XGL, I end up with Metacity as my window decorator, and can't even figure out how to change the GTK themes. (And the default look like it was made in 1992 or something.) Changing GTK themes as usual has no effect.

I like a lot of the themes in the Compiz section of Gnome-Look.org. Obviously, you don't do it within Metacity's theme changer.

Do I want to be using Emerald, or do I have other options? (I'm having problems with Emerald...)

Can anyone help one poor, confused sap? Thanks :)

EDIT: Okay, Gnome-Look's Compiz section is cgwd themes. From what I've found, cgwd is no more. Is that correct? What should I be using instead?

---

### Post by zanglang on 2007-07-28
Yeah, you can use Emerald, just change your compiz startup command to
> compiz --replace -c emerald
Be sure to install 'emerald' and 'emerald-themes' first though!

For GTK themes you can change them from System > Preferences > Theme. In most cases you can just drag the .zip you downloaded off Gnome-Look and drop it over the Theme window to install the theme, and then select it to switch to it.

Not sure about your shutdown button though... maybe you can just readd it to your panel?

---

### Post by fogster on 2007-07-28
> **zanglang said:**
> For GTK themes you can change them from System > Preferences > Theme. In most cases you can just drag the .zip you downloaded off Gnome-Look and drop it over the Theme window to install the theme, and then select it to switch to it.

I can't, though. I can change the Metacity window decorations that way, but changing the GTK theme has no effect. I don't get any errors, it just doesn't do anything. Prior to XGL+Compiz, I could change them fine and had a nice GTK theme that didn't look like it predated Windows 95.

Any idea what's going on? Is it related somehow to me starting gnome-session?

EDIT: Okay, I'm able to start Emerald. It has a nice border. But I can't change themes. The Emerald Theme Manager shows me lots of nice ones, but clicking them, much like trying to change my GTK theme, has no effect. Even logging out and back in, I'm still using the same Emerald theme that I was when I first started, despite having selected a new one.

---

### Post by windrant on 2007-07-29
Hey, I was having the same problems with the GTK theme sucking with Compiz-Fusion and XGL desktop.  I found a solution off the Compiz website.

See if this works for you: Hit Alt-F2 to bring up the "Run Application" dialog and enter gnome-settings-daemon and click run.

It should bring your chosen GTK theme up right away.  If so, then add that command to your sessions.

Using emerald for me is still hit or miss. Some times it works and sometimes not. I always have to log out and log back in again to have the theme kick in. So I'm following this thread to see if anybody else has more advice.  I too am missing the shutdown as well.

Hopefully that helps!

---

### Post by fogster on 2007-08-06
That's it! (The gnome-settings-daemon bit.)

Thanks windrant.

---

