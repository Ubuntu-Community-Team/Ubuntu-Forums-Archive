---
title: "dereferencing symbolic link"
date: 2009-11-12
forum: Desktop Environments
---

### Post by election on 2009-11-12
Hi

is there a command  for listing all the links pointing to a specific file??

For eg. i have *abc.so* file in [I]/usr

[/I]and there is a symbolic link to this *abc.so* in */home* say *mylink* 
and another symbolic link to the same abc.so in */opt* say *mylink2*
i need a command *mycmd* such that
if i type *mycmd* [I]/usr/abc.so
[/I]then it should give output as
*/usr/abc.so* <-- */home/mylink*
*/usr/abc.so* <-- */opt/mylink2*

Thanks
[COLOR=#888888][[IMG]http://twitter.com/favicon.ico[/IMG]]("http://search.twitter.com/search?q=is%20there%20a%20command%20in%20GNU%2FLinux%20for%20knowing%20the%20links%20pointing%20to%20a%20specific%20file%3F%3F%0A%0AFor%20eg.%20i%20have%20abc.so%20file%20in%20%2Fusr%0A%0Aand%20there%20is%20a%20symbolic%20link%20to%20this%20abc.so%20in%20%2Fhome%20say%20mylink%0Ai%20need%20a%20command%20mycmd%20such%20that%0Aif%20i%20type%20mycmd%20%2Fusr%2Fabc.so%0Athen%20it%20should%20give%20output%20as%0A%2Fusr%2Fabc.so%20%3C--%20%2Fhome%2Fmylink%0A")[[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=is%20there%20a%20command%20in%20GNU%2FLinux%20for%20knowing%20the%20links%20pointing%20to%20a%20specific%20file%3F%3F%0A%0AFor%20eg.%20i%20have%20abc.so%20file%20in%20%2Fusr%0A%0Aand%20there%20is%20a%20symbolic%20link%20to%20this%20abc.so%20in%20%2Fhome%20say%20mylink%0Ai%20need%20a%20command%20mycmd%20such%20that%0Aif%20i%20type%20mycmd%20%2Fusr%2Fabc.so%0Athen%20it%20should%20give%20output%20as%0A%2Fusr%2Fabc.so%20%3C--%20%2Fhome%2Fmylink%0A")[[IMG]http://static.smarterfox.com/media/wiki-favicon-sharpened.png[/IMG]]("http://smarterfox.com/wikisearch/search?q=is%20there%20a%20command%20in%20GNU%2FLinux%20for%20knowing%20the%20links%20pointing%20to%20a%20specific%20file%3F%3F%0A%0AFor%20eg.%20i%20have%20abc.so%20file%20in%20%2Fusr%0A%0Aand%20there%20is%20a%20symbolic%20link%20to%20this%20abc.so%20in%20%2Fhome%20say%20mylink%0Ai%20need%20a%20command%20mycmd%20such%20that%0Aif%20i%20type%20mycmd%20%2Fusr%2Fabc.so%0Athen%20it%20should%20give%20output%20as%0A%2Fusr%2Fabc.so%20%3C--%20%2Fhome%2Fmylink%0A&locale=en-US")[[IMG]http://static.smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]]("http://www.oneriot.com/search?p=smarterfox&ssrc=smarterfox_popup_bubble&spid=8493c8f1-0b5b-4116-99fd-f0bcb0a3b602&q=is%20there%20a%20command%20in%20GNU%2FLinux%20for%20knowing%20the%20links%20pointing%20to%20a%20specific%20file%3F%3F%0A%0AFor%20eg.%20i%20have%20abc.so%20file%20in%20%2Fusr%0A%0Aand%20there%20is%20a%20symbolic%20link%20to%20this%20abc.so%20in%20%2Fhome%20say%20mylink%0Ai%20need%20a%20command%20mycmd%20such%20that%0Aif%20i%20type%20mycmd%20%2Fusr%2Fabc.so%0Athen%20it%20should%20give%20output%20as%0A%2Fusr%2Fabc.so%20%3C--%20%2Fhome%2Fmylink%0A")[/COLOR]

---

