---
title: "Problems with colours on desktop popup notifications"
date: 2011-03-03
forum: Desktop Environments
---

### Post by UeB on 2011-03-03
When you hover your cursor over in icon often you get some info about it.

Now I have the problem that this info is unreadable in all the KDE apps I use and in Skype. (see the sceenshot I attached to see what I mean)

I uses Ubuntu 10.10 with Gnome the radiance theme.
When switch to another theme and then immediately switch back to radiance the colours are good but after a reboot I get back the unreadable colours.

What can I do to solve this problem?

Thank you in advance.

---

### Post by UeB on 2011-03-04
shameless self bump

Anybody knows anything about the colours of the pop-up messages?

---

### Post by UeB on 2011-03-07
somebody? something?

---

### Post by UeB on 2011-03-15
I tried to use other themes and I noticed that the problem I described in my fist post only appears when I uses radiance or ambiance. So my workaround at the moment is to use other themes like glider or clearlooks, but I still would be interested in a real solution so I can use radiance again, because I like it most of all the theme that ship by default with ubuntu 10.10.

---

### Post by judedawson on 2011-03-15
Hi UeB, 

I have the exact same problem with my Skype and I'm running the 'radiance' theme, too. 

I guess I just got used to it. Too lazy, I guess... ;)

---

### Post by Krytarik on 2011-03-15
Sorry, I was subscribed to your thread, but I didn't dare to hang in until now because I don't use KDE apps at all.

Thanks for trying other themes, that at least gave a hint at what I have to look.
I don't have the theme "Glider", but of course "Clearlooks", and the difference between those and Ambiance/Radiance is that the latter use the "new" tooltip style and the Murrine engine, with the option "rgba", whereas "Clearlooks" doesn't.

So, to disable the new tooltip style and/or Murrine/"rgba" option, and make them hopefully work with KDE apps, simply change what I marked, with Radiance as the example, play a bit around with the options to figure what the actual culprit is:

```
sudo cp /usr/share/themes/Radiance/gtk-2.0/gtkrc /usr/share/themes/Radiance/gtk-2.0/gtkrc-original
gksudo gedit /usr/share/themes/Radiance/gtk-2.0/gtkrc
```/usr/share/themes/Radiance/gtk-2.0/gtkrc:
```
    #######################
    # Style Properties
    #######################
[B][COLOR=Red]    #GtkWidget::new-tooltip-style = 1
[/COLOR][/B]    GtkButton::child-displacement-x = 1
    GtkButton::child-displacement-y = 1
    GtkButton::default-border = { 0, 0, 0, 0 }

``````
style "tooltips" {
    xthickness = 4
    ythickness = 4

    bg[NORMAL]        = @tooltip_bg_color
    fg[NORMAL]        = @tooltip_fg_color
[B][COLOR=Red]    #bg[SELECTED]      = "#000000"
[/COLOR][/B]
[B][COLOR=Red]    #engine "murrine" {
    #    rgba = TRUE
    #}
[/COLOR][/B]}

```

---

### Post by UeB on 2011-03-15
@Krytarik
Thanks for your reply.
I made the changes you proposed to the file
/usr/share/themes/Radiance/gtk-2.0/gtkrc
but it did not have any effect.
When switching to radiance the colours of the tooltip of kde apps and skype look good, but after a reboot they look as in my posted sceenshots.

---

### Post by Krytarik on 2011-03-15
Ok, unfortunately I can't compare, or at least I don't know which KDE apps are installed by default and don't want to check all apps. ;-)

But maybe it's because of the general use of Murrine by those themes. So please try the following: Grab a copy of one of my themes (link in my signature), all of them don't use the Murrine engine at all, but use the new tooltip style. And no, I don't want to promote my themes by that way, it's just easier because I know them. ;-)

---

### Post by UeB on 2011-03-16
Dear Krytarik,

I tried your theme "iMetal Leopard Krytarik light"
but it has the same behaviour as ambiance and radiance: skype and kde tooltips readable when switching to the theme. But not readable after a reboot.

---

### Post by Krytarik on 2011-03-16
> **UeB said:**
> 
I tried your theme "iMetal Leopard Krytarik light"
but it has the same behaviour as ambiance and radiance: skype and kde tooltips readable when switching to the theme. But not readable after a reboot.
Then it is definitely the *new tooltip style*! Are you sure, that you really disabled it!?

---

### Post by UeB on 2011-03-16
> **Krytarik said:**
> Are you sure, that you really disabled it!?

If by disable you mean comment out the line GtkWidget::new-tooltip-style = 1 in the file /usr/share/themes/Radiance/gtk-2.0/gtkrc then yes I am sure I did it. (just looked at the file again)

---

### Post by Krytarik on 2011-03-16
> **UeB said:**
> If by disable you mean comment out the line GtkWidget::new-tooltip-style = 1 in the file /usr/share/themes/Radiance/gtk-2.0/gtkrc then yes I am sure I did it. (just looked at the file again)
Also outcomment the line of "bg[SELECTED]", like mentioned in the second code frame.

---

### Post by UeB on 2011-03-16
yes, this is what it looks like in my file:

style "tooltips" {
	xthickness = 4
	ythickness = 4

	bg[NORMAL]        = @tooltip_bg_color
	fg[NORMAL]        = @tooltip_fg_color
	#bg[SELECTED]      = "#000000"

	#engine "murrine" {
	#	rgba = TRUE
	#}
}

I also attached the full file

---

### Post by Krytarik on 2011-03-16
I re-checked your initial post: Is it correct, that the tooltips even change their colors, depending on which button/whatever you mouseover? The last, most right screenshot, is that the look before restart?

Also, please check if you have a "~/.kderc". If so, please post its content.

And, do you know which KDE apps are installed by default in the "Ubuntu" version, so that I can try it as well?

---

### Post by UeB on 2011-03-19
> **Krytarik said:**
> I re-checked your initial post: Is it correct, that the tooltips even change their colors, depending on which button/whatever you mouseover? The last, most right screenshot, is that the look before restart?

the right most is what a) evry tooltip looks like when I change to the radiance theme and b) what all the gnome apps sill look like after a reboot.
After the reboot the tooltip for skype and for kde apps change their colour to what you can see in the first 2 sceenshots. They stay that way until I change the theme again.
> 
Also, please check if you have a "~/.kderc". If so, please post its content.

No I do not have a file namend .kderc in my home directoy
> 
And, do you know which KDE apps are installed by default in the "Ubuntu" version, so that I can try it as well?

I am not an expert on this but I think that Ubuntu tries to avoid KDE apps in the default installation and sticks to gnome apps as far as possible to get a coherent look and feel. Same with opposite sign for Kubuntu. So no, I do not know any KDE app in the default install. The once I use I installed via synaptik.

---

### Post by Krytarik on 2011-03-19
> **UeB said:**
> 
After the reboot the tooltip for skype and for kde apps change their colour to what you can see in the first 2 sceenshots.
Ok, but why are those two differently colored? Different themes?

---

### Post by UeB on 2011-03-19
> **Krytarik said:**
> Ok, but why are those two differently colored? Different themes?

No, same theme, still radiance but different "wrong" colours in skype and kde apps.

---

### Post by Krytarik on 2011-03-19
Now I definitely know that there is no KDE apps at all in the default "Ubuntu" installation, because every KDE app I try to install would pull the complete KDE backend with it.

But I will test it with Skype, since it is no KDE app.

---

### Post by Krytarik on 2011-03-19
I tested it with Skype earlier, and I don't have those issue, I did the same like you:
- chose the Radiance theme
- checked Skypes tooltips -> fine (like yours)
- rebooted
- checked again -> still fine

Questions:
- Do you have those issue also with Mozilla apps (if you use one), e.g. Firefox or Thunderbird?
- Does the issue get healed if you restart "gnome-settings-daemon"?
```
killall gnome-settings-daemon && gnome-settings-daemon && killall nautilus
```

---

### Post by UeB on 2011-03-20
> **Krytarik said:**
> I tested it with Skype earlier, and I don't have those issue, I did the same like you:
- chose the Radiance theme
- checked Skypes tooltips -> fine (like yours)
- rebooted
- checked again -> still fine

Questions:
- Do you have those issue also with Mozilla apps (if you use one), e.g. Firefox or Thunderbird?

I use thunderbird and firefox very often and I never had this problem there
> 
- Does the issue get healed if you restart "gnome-settings-daemon"?
```
killall gnome-settings-daemon && gnome-settings-daemon && killall nautilus
```
Yes but I does so by switching to a black on brown colour scheem for all tooltip and not by going back to the white on black tooltip colours of the radiance theme

---

### Post by UeB on 2011-03-20
I found another curiosity regading the skype tookip:

In the Options of skype you can choose "Stil wählen" in the section "Allgemein"*. If I choose the style "plastique" I get the prolems with the wrong tooltip colours if I choose "GTK+" I do NOT get the problem with the tooltip colours.


*I have the german version of skype

---

### Post by Krytarik on 2011-03-20
> **UeB said:**
> 
In the Options of skype you can choose "Stil wählen" in the section "Allgemein"*. If I choose the style "plastique" I get the prolems with the wrong tooltip colours if I choose "GTK+" I do NOT get the problem with the tooltip colours.

Oh, then you must have switched those option by yourself, since it is apparently not set that way by default. I have to admit that I didn't check its options after I saw that the tooltips are fine.

Still an issue with the KDE apps. I know that one can choose a similar option when running full KDE. Please do a websearch about the respective config file.

---

### Post by UeB on 2011-03-22
I solved the problem.
I did what is  described in this thread:
[http://ubuntuforums.org/showthread.php?t=1580266]("http://ubuntuforums.org/showthread.php?t=1580266")
after a
```
sudo apt-get install systemsettings
```
one has a GUI to change lots of KDE related things, when one changes the tooltip colours there to what it should be (white on black in case of radiance) it stays.

---

