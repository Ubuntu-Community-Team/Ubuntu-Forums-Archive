---
title: "Problem With Theme Changing"
date: 2009-06-12
forum: General Help
---

### Post by demonoidmaster on 2009-06-12
When I Open The Theme Manager I Get This Output At The Bottom

**"this theme will not look as intended because the required window manager theme 'Human' is not installed"**


Any Answers ???

---

### Post by jenkinbr on 2009-06-12
Open a terminal (Applications >> Accessories >> Terminal)

Run the code

```
sudo apt-get install human-theme
```

See if that helps.

---

### Post by demonoidmaster on 2009-06-12
It Already Was Installed... And Thats The Default Theme When Installing Ubuntu......

So Idk Why The Theme Manager Doesnt Find Any Themes....

---

### Post by jimv on 2009-06-12
Did you download this off Gnome-look.org?  If so, perhaps you could contact the author of the theme to see what the problem is.

---

### Post by demonoidmaster on 2009-06-12
Wow...Really ?

READ My Last Post CAREFULLY...

When Installing Ubuntu 9.04 (Jaunty), This Theme Is Installed And Is Default

So, I Know I Have This Damn Theme Installed... I Aint Dumb

And My Overall Problem Is That I Cannot Select Any Themes Because None Appear In The Theme Selector

And Also.. My Panel Bars Dont Have That Thin Black Shadow When They Are Transparent

**Reference - **( Right Click Panel¬
                                 .......................................Properties¬
                                          ...............................................Background¬
..........................................................Solid Color --> Transparent )

---

### Post by jenkinbr on 2009-06-12
> **demonoidmaster said:**
> Wow...Really ?

READ My Last Post CAREFULLY...

When Installing Ubuntu 9.04 (Jaunty), This Theme Is Installed And Is Default

So, I Know I Have This Damn Theme Installed... I Aint Dumb

And My Overall Problem Is That I Cannot Select Any Themes Because None Appear In The Theme Selector

And Also.. My Panel Bars Dont Have That Thin Black Shadow When They Are Transparent

**Reference - **( Right Click Panel¬
                                 .......................................Properties¬
                                          ...............................................Background¬
..........................................................Solid Color --> Transparent )
As far as the theme goes, there was a chance that the theme could have been uninstalled. Having you install it served as a test to see if for some reason it was uninstalled, and if that was the case, it would re-install it.

As for the shadow on the panels, not sure what you mean by that exactly.  Do you have desktop effects enabled?  Outside Compiz-Fusion, I don't know how you could get a shadow around your panels.

As for the theme manager issue, I have needed to delete my .theme folder in the past (I usually rename it first, before removing it completely).
[list][*]Open the file browser to your home directory ( Places >> Home Folder )
[*]Press CTRL + H to show hidden files --OR-- click ( View >> Show hidden Files )
[*]Select the folder named .theme
[*]Right-click >> Rename --OR-- press F2
[*]Rename the folder to .theme_old[/list]
Sorry if this doesn't help, but I don't know everything either.

---

### Post by jimv on 2009-06-12
You could try reinstalling all of the themes:

sudo apt-get install --reinstall gnome-themes gnome-themes-ubuntu gnome-themes-selected gnome-themes-extras

---

### Post by demonoidmaster on 2009-06-12
Ok, Nvm...Fixed It

Actualy It Wasnt Any Of The Themes.... All Of The Themes Where Installed Properly


Its Just Some Files That Got Uninstalled (Must Of Been During Removal Of Easytag And Stuff)

---

### Post by jenkinbr on 2009-06-12
> **demonoidmaster said:**
> Ok, Nvm...Fixed It

Actualy It Wasnt Any Of The Themes.... All Of The Themes Where Installed Properly


Its Just Some Files That Got Uninstalled (Must Of Been During Removal Of Easytag And Stuff)
That's odd...are you sure you didn't mess with anything?  Because software packages that have conflicting file paths should be conflicting packages.



I've mucked around with things in the past and have messed things up, requiring a reinstallation of some packages, or worse - the whole system.

That taught me a lesson - don't mess with something that you don't know, cause you might break it.

Glad to hear your problem is solved. :)

---

### Post by colau on 2009-06-12
> **jimv said:**
> you could try reinstalling all of the themes:

Sudo apt-get install --reinstall gnome-themes gnome-themes-ubuntu gnome-themes-selected gnome-themes-extras
+1;)

---

### Post by jenkinbr on 2009-06-12
> **colau said:**
> +1;)
Miss something?
> **demonoidmaster said:**
> Ok, Nvm...Fixed It

The OP's problem is solved.

---

### Post by NilsE on 2009-06-12
Looks to me like what cured the problems for these folks was not reinstalling the themes but reinstalling the theme-extras.

The OP's original message was not that the theme was missing but the theme "engine".  Themes are written based on "engines" and there can be many different themes that use the same engine.  There was a problem in either Hardy or Intrepid where someone renamed one or more of the engines but the themes were not updated to reflect the new name. This seemed to be very similar.

---

