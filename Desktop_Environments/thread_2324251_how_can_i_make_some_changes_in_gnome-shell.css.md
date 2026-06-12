---
title: "how can i make some changes in gnome-shell.css"
date: 2016-05-12
forum: Desktop Environments
---

### Post by srk31 on 2016-05-12
hey everybody,
like i said i want to make changes in gnome-shell file but i don't know  what line i have to change, if you can help me that will be great.

ok so i want to stufs like this :  [IMG]https://drive.google.com/file/d/0B_4GuJHiIXcXT09tcmpLTDZ1d28/view[/IMG]

---

### Post by buzzingrobot on 2016-05-14
I believe recent Gnome versions use a quasi-compiled format for their CSS, at least for the default Adwaita theme. It cannot be directly edited. You'd need to consult Gnome documentation for advice on editing the source and rebuilding the theme.

AFAIK, if you identify the specific CSS elements you want to alter, you can create your own CSS code that affects those elements, place it in the correct location in your home folder, and CSS's cascading attribute *should* override the default settings with yours.

---

### Post by vasa1 on 2016-05-14
> **buzzingrobot said:**
> I believe recent Gnome versions use a quasi-compiled format for their CSS, at least for the default Adwaita theme. It cannot be directly edited. You'd need to consult Gnome documentation for advice on editing the source and rebuilding the theme.

AFAIK, if you identify the specific CSS elements you want to alter, you can create your own CSS code that affects those elements, place it in the correct location in your home folder, and CSS's cascading attribute *should* override the default settings with yours.

It's not really clear what OP wants to do. OP mentions *gnome-shell.css* and talks of wanting "to make changes in gnome-shell file". That's not really much to go on.

---

### Post by srk31 on 2016-05-14
sorry, I had not seen that the image was not appeared, here is the result of what I want to get : [https://drive.google.com/file/d/0B_4GuJHiIXcXT09tcmpLTDZ1d28/view?pref=2&pli=1](https://drive.google.com/file/d/0B_4GuJHiIXcXT09tcmpLTDZ1d28/view?pref=2&pli=1)   
thanks

---

### Post by vasa1 on 2016-05-14
The image appeared just fine even in your first post. There's an apple in the top left corner and the date on the screen is 19th October and we're in May.

But that doesn't explain what *exactly* you want to achieve and it's possible that it may not be gnome-shell.css that needs to be changed but something else, maybe your gtk3 theme?

And if it is gnome-shell.css that you need to tweak, as buzzingrobot indicated, editing it is no longer a trivial matter in recent GNOME versions. See [https://thebreakfastpost.com/2015/07/09/replacing-the-gnome-shell-font-in-gnome-3-16/](https://thebreakfastpost.com/2015/07/09/replacing-the-gnome-shell-font-in-gnome-3-16/) for instance.

---

### Post by srk31 on 2016-05-15
first of all thank you for the link it is very useful, ok this is my fault I forget to specify what I wanted, forgetting the apple and the date, the name of the theme is "dark mode", you can find it on gnome-look and it works great in gnome 3.18. 
I have my own theme that I personalize, it has the poweroff button grey surrounded by blue and I would like to have the same button poweroff as that of the image with the color red. and why not also give other colors to restart and cancel buttons.

I hope that I am explicit, thanks again.

---

### Post by vasa1 on 2016-05-15
> **srk31 said:**
> first of all thank you for the link it is very useful, ok this is my fault I forget to specify what I wanted, forgetting the apple and the date, the name of the theme is "dark mode", you can find it on gnome-look and it works great in gnome 3.18. 
I have my own theme that I personalize, it has the poweroff button grey surrounded by blue and I would like to have the same button poweroff as that of the image with the color red. and why not also give other colors to restart and cancel buttons.

I hope that I am explicit, thanks again.

Can you please post the exact link to "dark mode"?

And you mention your "own theme". Can you provide the output of *ls -R /path/to_your_own_theme*? Does it have *gnome-shell.css*?

---

### Post by srk31 on 2016-05-15
hey, the link for "dark mode" theme is : [http://gnome-look.org/content/show.php/Dark+Mode?content=166387](http://gnome-look.org/content/show.php/Dark+Mode?content=166387).

my theme is a mixture of several theme and, of course, that gnome-shell.css is here, I'm working on what in your opinion?

anyway, I succeed, the job is done.

this is the lines i've changed and added :

_**change the values of "modal-dialog"   to this :**_

.modal-dialog {

                /*shoutdown*/


    background-color: rgba(0.0, 0.0, 0.0, 0.7);
    border: 2px solid rgba(60, 155, 155, 1.0);
    border-radius: 5px;
    box-shadow: 0px 11px 12px rgba(74,144,217,0.5);
    color:#efefef

}


**_and add this at the end of the script  :_**


/* Poweroff */

.end-session-dialog .modal-dialog-linked-button:last-child {
    background-gradient-direction:vertical;
    background-gradient-start: rgb(241,7,7);
    background-gradient-end: rgb(190,7,7);
    color: #fefefe;}
.end-session-dialog .modal-dialog-linked-button:last-child:focus,
.end-session-dialog .modal-dialog-linked-button:last-child:hover {
    background-gradient-direction:vertical;
    background-gradient-start: rgb(255,63,63);
    background-gradient-end: rgb(241,7,7);
}
.end-session-dialog .modal-dialog-linked-button:last-child:active {
    background-gradient-direction:none;
    background-color: rgb(241,7,7);
    box-shadow: inset 0px 2px 3px rgba(0,0,0,.25);

}

this is the result :  

[https://drive.google.com/open?id=0B_4GuJHiIXcXclFYZ1ZUTGpsaFE](https://drive.google.com/open?id=0B_4GuJHiIXcXclFYZ1ZUTGpsaFE)


remains to do the same thing for the other two button and it is good  sorry for the inconvenience, and thank you for your help

---

