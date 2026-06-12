---
title: "Dark Themes and Firefox userContent.css"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by hedonistic.heathen on 2007-07-25
I'd appreciate it if folks who are running dark themes and have made modifications to firefox's forms.css (/usr/lib/firefox/res/) or userContent.css (/.mozilla/firefox/**.default/chrome) would post those files (might include a screenshot or comments on how forms are appearing).

I'm using the [onux dark theme]("http://www.gnome-look.org/content/show.php/Onux?content=58118") (best dark theme I've found by the way - the green variation is great) and [firefox widgets]("http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets").  I've looked at the directions and modified css files included with the Neutronium and [H-K]("http://gnome-look.org/content/show.php/H-K+suite+gtk2?content=57433") themes and have managed to create a userContent.css file based on those and the firefox widget's modifications, but I can't seem to change the color of check boxes or drop-down lists.  Buttons, radio buttons, and text boxes all look fine, but my check boxes and drop-down lists are still black - they're functional and all, but they're a bit of an eye sore.

I don't know a thing about css, but here's my userContent.css as of now (I pretty much just tried typing white wherever I could in the checkbox and drop-down list portions of the code hoping that would have an effect, so this probably needs cleaned up):

```

/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border: 1px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-right-colors: ThreeDShadow Window;
  -moz-border-bottom-colors: ThreeDShadow Window;
  -moz-border-left-colors: ThreeDShadow ThreeDHighlight;
  background-color: white;	
  color: black;			
}

/* Buttons */

input[type="button"],
input[type="submit"],
input[type="reset"],
button,
select {
    color: ButtonText;
/*  background-color: Window; */
  background-color: #eeeeee;
  color: black;
  background: #eeeeee url("/form-widgets/button.png") repeat-x bottom right;
  border: 1px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
  -moz-border-radius: 1px;
}

input[type="button"]:hover,
input[type="submit"]:hover,
input[type="reset"]:hover,
button:hover {
    color: ButtonText;
    /*  background-color: Window; */
    background-color: #eeeeee ThreeDHighlight;
    color: black;
  background: #eeeeee url("/form-widgets/button.png") repeat-x bottom right;
  border: 1px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
  -moz-border-radius: 1px;
}

/* Radio buttons */

input[type="radio"] {
  height: 13px !important;
  width: 13px !important;
  background-image: url("form-widgets/radio.png") !important;
  border: none !important; 
/*  background-color: transparent !important;*/
  background-color: white ! important;
}

input[type="radio"]:checked {
  background-image: white url("form-widgets/radio-checked.png") !important;
}

input[type="radio"]:focus,
input[type="radio"]:active,
input[type="radio"]:hover:active {
  border:none !important; 
}

input[type="radio"]:hover:active {
/*  background-color: transparent !important; */
    background-color: white ! important;
  background-image: url("form-widgets/radio-active.png") !important;
}

input[type="radio"]:hover:active:checked {
    background-image: url("form-widgets/radio-active-checked.png") !important;
}

input[type="radio"][disabled],
input[type="radio"][disabled]:hover,
input[type="radio"][disabled]:active,
input[type="radio"][disabled]:hover:active {
  border: none !important;
/*  background-color: transparent !important; */
  background-color: white ! important;
  background-image: url("form-widgets/radio-disabled.png") !important;
}

*::-moz-radio {
  border: none !important;
/*  background-color: transparent !important; */
  background-color: white ! important;
}

/* Checkboxes */

input[type="checkbox"] {
  width: 12px !important;
  height: 12px !important;
  border-width: 0 !important;
  background-image: white url("form-widgets/checkbox.png") !important;
/*  background-color: -moz-Field; */
  background-color: ThreeDFace ! important;
}

input[type="checkbox"]:checked {
  background-image: url("form-widgets/checkbox-checked.png") !important;
}

/* Dropdowns  */

select,
select:not([size]),
select[size="0"],
select[size="1"] {
  color: ButtonText !important;
/*  background-color: Window; */
  background-color: white ! important;
  background: white url("form-widgets/button.png") repeat-x bottom right !important ;
  /*border: 2px solid ThreeDShadow; 
  -moz-border-top-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-right-colors: ThreeDShadow Window;
  -moz-border-bottom-colors: ThreeDShadow Window;
  -moz-border-left-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-radius: 1px; */
}

select > input[type="button"]{
  width: 6px;
  border: none;
  background-color: white ! important;
  background: white url("form-widgets/droparrow.png") no-repeat center center !important;
}

select > input[type="button"]:focus {
}

*|*::-moz-dropdown-list {
  z-index: 2147483647;
  background-color: white !important;
  -moz-user-select: none;
  position: static !important;
  float: none !important;

  border: 1px outset black !important;
} 

```

---

### Post by gavintlgold on 2007-07-26
Someone kindly commented on my Emerald theme with instructions to do just that.

[http://www.beryl-themes.org/content/show.php/Grey+Neu?content=60824](http://www.beryl-themes.org/content/show.php/Grey+Neu?content=60824) ... see Proton's comment.

---

### Post by badkungfu on 2007-10-07
The author of the Divinorum theme included a good userContent.css file:
[http://xfce-look.org/content/show.php/Divinorum?content=65533](http://xfce-look.org/content/show.php/Divinorum?content=65533)

---

