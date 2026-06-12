---
title: "Firefox: Disabling intense white (#FFFFFF)  website background colors"
date: 2009-05-30
forum: General Help
---

### Post by Markhor on 2009-05-30
Hello. Does anyone know of an add-on or script which when encountering a website with the background #FFFFFF = severe eye-strain (i.e. google & google search pages), will swap with a less intense color?

Also, I noticed the Firefox add-on 'Anycolor' is not available for Linux users. Does anyone know of a substitute add-on?

---

### Post by floppit on 2009-05-30
> **Markhor said:**
> Hello. Does anyone know of an add-on or script which when encountering a website with the background #FFFFFF = severe eye-strain (i.e. google & google search pages), will swap with a less intense color?

Also, I noticed the Firefox add-on 'Anycolor' is not available for Linux users. Does anyone know of a substitute add-on?

I think [NoSquint]("https://addons.mozilla.org/sv-SE/firefox/addon/2592") should be able to help solve your problem.  :D

---

### Post by lovinglinux on 2009-05-30
Install [Stylish](https://addons.mozilla.org/en-US/firefox/addon/4902) extension, then create a new script like this.

```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document url-prefix(http) {

body{
background:#000 !important;
opacity:.7 !important;
}

}
```

Another alternative, would be to install [Jetpack](https://addons.mozilla.org/en-US/firefox/addon/12025) extension, then type *about:jetpack* in the address bar, then click "Develop" in the jetpack page and paste the code below into the text area and click "try out this code":

```
jetpack.statusBar.append({
  html: 'Dim<input type="checkbox">',
  width: 60,
  onReady: function(widget){
    $("input", widget).click(function(){
      if( this.checked ){
      $(jetpack.tabs.focused.contentDocument)
        .find("body")
        .css({backgroundColor:"black"})
        .animate({opacity:.5});
      }
      else $(jetpack.tabs.focused.contentDocument)
        .find("body")
        .css({backgroundColor:""})
        .animate({opacity:100});
    });
  }
});

```

This will add a "Dim" select box in the status bar that you can activate/deactivate easily.

See the result attached.

---

### Post by Markhor on 2009-05-30
Perfect Solutions! Thanks!

---

