---
title: "Ubuntu-AR Chromium App + Source"
date: 2011-11-11
forum: Comunidad
---

### Post by juancarlospaco on 2011-11-11
[SIZE="3"]Ubuntu-AR Chromium App *(Beta)* + Source[/SIZE]

[LIST]
[*]Es basicamente los mismos Links Utiles del [Icono Unity de Ubuntu-AR]("http://ubuntuforums.org/showthread.php?t=1850238") :P
[/LIST]

Source:
```

<!DOCTYPE html>
<html lang="es">



<!-- BEGIN MANIFEST.JSON CORE CONFIG -- Licence: GPLv3
{
  "name": "Ubuntu-AR",
  "version": "0.1",
  "description": "Obtener info de Ubuntu-AR | Get info from Ubuntu-AR",
  "icons": { "16" : "img/icon16.png",
             "48" : "img/icon48.png",
             "128" : "img/icon128.png" },
  "homepage_url": "http://www.ubuntu.org.ar",
  "permissions": [ "http://*" ],
  "browser_action": {
    "default_icon": "img/icon16.png",
    "default_title": "Ubuntu-AR",
    "default_popup": "web.html"
  }
}
 -- END MANIFEST.JSON CORE CONFIG -->



<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <META NAME="ROBOTS" CONTENT="INDEX, NOFOLLOW">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- CSS3 STYLES -->
  <style>
  body {
    color: white;
   	font: bold 12px ubuntu;
    background:
		-webkit-radial-gradient(white 2%, transparent 8%),
		-webkit-radial-gradient(white 2%, transparent 8%),
		white;
	background-position: 0 0, 150px 150px;
	-webkit-background-size: 23px 23px;
    border-radius: 0px 0px 0px 0px;
    text-align: center;
    margin: 0;padding: 0;border: 0;font-size: 100%;font: inherit;
    vertical-align:baseline;overflow:none;
  }
  iframe {
    border-radius: 20px;
    padding: 0px 0px;
    border: 2px dotted black;
  }
  select, button {
    display: inline-block;
    text-align:center;
    text-shadow: none;
    text-transform: uppercase;
	-webkit-border-radius: 12px;
	-webkit-box-shadow: 2px 2px 3px #999;
	border: solid 3px rgb(110,110,110);
	background-image: -webkit-gradient(linear, left top, left bottom, from(rgba(234,234,234,0.90)), color-stop(0.5, rgba(195,195,195,0.70)), color-stop(0.5, rgba(166,166,166,0.70)), to(rgba(167,167,167,0.80))); 
	color: #000;
   	font: bold 12px ubuntu;
	padding: 1px 25px;
    cursor: pointer;
  }
  select:hover, button:hover {
    background-image: -webkit-gradient(linear, left top, left bottom, from(orange), to(red));
	color: #fff;
    text-align:center;
	text-shadow: #000 0 1px 0;
	-webkit-box-shadow: inset rgba(207,207,255,0.75) 0px 1px 1px;
   	font: bold 12px ubuntu;
	padding: 1px 25px;
    cursor: pointer;
  }
  </style>
</head>
<body>
  <FORM NAME="myform">
  <SELECT NAME="dest" SIZE=1 onChange="leapto(this.form)" onMouseover="buttonsnd.play();" >
  <OPTION SELECTED VALUE="">Elije 1 Link | Choose 1 Link
  <OPTION VALUE="http://www.ubuntu.org.ar">Ubuntu-AR Web
  <OPTION VALUE="http://uluga.ubuntuforums.org">Ubuntu-AR Foros
  <OPTION VALUE="http://webchat.freenode.net?channels=Ubuntu-ar&uio=OT10cnVlJjExPTI0Ng32">Ubuntu-AR Chat IRC
  <OPTION VALUE="http://twitter.com/ubuntuar">Ubuntu-AR Twitter
  <OPTION VALUE="http://identi.ca/group/ubuntuar">Ubuntu-AR Identi.ca
  <OPTION VALUE="http://wiki.ubuntu.com/ArgentinaTeam">Ubuntu-AR Wikis
  </SELECT>
  </FORM>
  <iframe width="700" height="480" name="CONTENT"></iframe>
  <input type="button" href="http://www.ubuntu.org.ar" target="_blank" >Ubuntu-AR Web</input>
  <!-- JS SCRIPTS -->
  <audio id="buttonsnd" src="click.ogg" type="audio/ogg" preload="auto" class="hidden"></audio>
  <script language="JavaScript" type="text/JavaScript" charset="utf-8" defer="defer">function leapto(form){var myindex=form.dest.selectedIndex;parent.CONTENT.location.href=(form.dest.options[myindex].value); }</script>
  <script language="JavaScript" type="text/JavaScript" charset="utf-8" defer="defer">var buttonsnd = document.getElementById('buttonsnd');buttonsnd.load();buttonsnd.volume=0.75;</script>
</body>
</html>

```

Licence: GPLv3


Screenshot y Archivo comprimido *(Descargar, Descomprimir, Doble Click)* :

---

### Post by guillermolisi on 2011-11-12
Juanca, es "eli**g**e", no "elije" :p

---

