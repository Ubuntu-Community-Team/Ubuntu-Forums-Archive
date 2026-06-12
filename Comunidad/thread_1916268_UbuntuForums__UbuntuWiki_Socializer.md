---
title: "UbuntuForums / UbuntuWiki Socializer"
date: 2012-01-27
forum: Comunidad
---

### Post by juancarlospaco on 2012-01-27
[SIZE="3"]UbuntuForums / UbuntuWiki Socializer[/SIZE]

[LIST]
[*]Agrega botones para compartir lo que estas leyendo/posteando en Twitter y Google Plus
[*] Agnostico al Idioma (es 1 boton y 1 numero)
[/LIST]



**[SIZE="2"]UBUNTUFORUMS.ORG:[/SIZE]**

```

// ==UserScript==
// @name       UbuntuForums Socializer
// @version    0.1
// @description  Adds TW and G+ Social Buttons
// @include    http://ubuntuforums.org/*
// @copyright  GPLv3, juancarlospaco@ubuntu.com 
// ==/UserScript==

function insertPlusOne(node) {
  var button = document.createElement("g:plusone"); 
  button.setAttribute("size", "small");
  node.appendChild(button);
  var po = document.createElement("script"); 
  po.type = "text/javascript"; 
  po.async = true;
  po.src = "https://apis.google.com/js/plusone.js";
  document.head.appendChild(po);
}

function insertTw(node) {
  var button = document.createElement("a"); 
  button.setAttribute("href", "http://twitter.com/share");
  button.setAttribute("class", "twitter-share-button");
  button.setAttribute("data-count", "small");  
  node.appendChild(button);
  var po = document.createElement("script"); 
  po.type = "text/javascript"; 
  po.async = true;
  po.src = "http://platform.twitter.com/widgets.js";
  document.head.appendChild(po);
}

insertPlusOne(document.getElementById("lastpost"));
insertTw(document.getElementById("lastpost"));

```

**[SIZE="2"]UBUNTU WIKI:[/SIZE]**

```

// ==UserScript==
// @name       UbuntuWiki Socializer
// @version    0.1
// @description  Adds TW and G+ Social Buttons
// @include    https://wiki.ubuntu.com/*
// @copyright  GPLv3, juancarlospaco@ubuntu.com 
// ==/UserScript==
function insertPlusOne(node) {
  var button = document.createElement("g:plusone"); 
  button.setAttribute("size", "small");
  node.appendChild(button);
  var po = document.createElement("script"); 
  po.type = "text/javascript"; 
  po.async = true;
  po.src = "https://apis.google.com/js/plusone.js";
  document.head.appendChild(po);
}
function insertTw(node) {
  var button = document.createElement("a"); 
  button.setAttribute("href", "http://twitter.com/share");
  button.setAttribute("class", "twitter-share-button");
  button.setAttribute("data-count", "small");  
  node.appendChild(button);
  var po = document.createElement("script"); 
  po.type = "text/javascript"; 
  po.async = true;
  po.src = "http://platform.twitter.com/widgets.js";
  document.head.appendChild(po);
}

insertPlusOne(document.getElementsByTagName("h1")[0]);
insertTw(document.getElementsByTagName("h1")[0]);

```



Probado en Firefox, Chromium y Chrome; deberia funcionar en cualquiera,
se guarda el codigo como "socializer.user.js" y se lo abre con el navegador, intentara instalarlo como un plugin mas.

**Screenshots:**

---

