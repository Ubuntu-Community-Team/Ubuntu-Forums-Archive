---
title: "Problems with Metacity and Firefox"
date: 2007-02-28
forum: Desktop Environments
---

### Post by AlcoJaguar on 2007-02-28
I recently began using [Darker Theme]("http://www.gnome-look.org/content/show.php?content=32768") with Metacity and it looks very good, but I have one problem with it overriding firefox default colors. One of the biggest problems actually manifests in the forums as it turns text inputs black and the text within white. Well on the forums somewhere in the CSS text in text boxes and inputs is explicitly set white so all my text boxes are white on white and I have to disable CSS in order to even see what I type in a field (or else ditch this theme which I really don't want to do, it's the best I've seen so far). Is there a way to exempt certain applications from using theme colors (I have tried disabling the use_system_colors option in about:config in Firefox to no avail and I have also tried to set up my own user style sheets to override the theme with still no luck)?

---

### Post by AlcoJaguar on 2007-03-01
Bump... I can wait, hehe.

---

### Post by AlcoJaguar on 2007-03-01
After digging around gnome-look.org I found an answer to my dilemma. If you're having trouble with a dark theme changing the colors of text boxes on web pages you can color the directions contained in the [Neutronium Theme - http://www.gnome-look.org/content/show.php?content=46153]("http://www.gnome-look.org/content/show.php?content=46153") to rectify the problem. Here's an excerpt taken directly from the instructions.

------------------
Firefox:

If web forms and controls appear dark and unreadable you need to edit the css files that Firefox uses. The file location may vary on different linux distributions.

1. Backup the original file:
sudo mv /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms_backup.css

2. Replace it with the provided forms.css
sudo mv /<downloaded location>/Neutronium-GTK2/forms.css /usr/lib/firefox/res/forms.css

3. Then you need to edit html.css:
sudo gedit /usr/lib/firefox/res/html.css

Around line 60, change:

body {
  display: block;
  margin: 8px;
}

To:

body {
  background-color: white;
  color: black;
  display: block;
  margin: 8px;
}

Save the file, then restart Firefox, and you should have standard colours.
------------------

Of course you need the forms.css from the Neutronium Theme package (I'm not sure if he did anything to the forms.css or just included a fresh copy, I didn't check).

---

