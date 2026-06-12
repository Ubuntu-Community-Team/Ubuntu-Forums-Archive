---
title: "wget downloads only part of a URL content"
date: 2009-01-26
forum: General Help
---

### Post by GabrielWolff on 2009-01-26
I am trying to download the content of the following URL: [http://epsapublishing.com](http://epsapublishing.com)
When using wget and typing in ```
wget -r http://epsapublishing.com
```, it will download only the following folders: ```
gabriel@gabriel-laptop:~/epsapublishing.com$ ls
css  images  includes  index.html  js  swf
gabriel@gabriel-laptop:~/epsapublishing.com$ 
```
while what I am actually interested in are a lot of pdf files at that URL. The pdfs are located at adresses like the following one: ```
http://epsapublishing.com/index.php?modulo=obras&accion=obras_pop_up_descarga&idobras=1300&tipo=partitura&archivo=radaelli/RADAELLI_ZambadeTilo_Quarteto.pdf
```
 
When directing wget directly to a file I want to download, the file will not be downloaded, but rather a plain text document only, as for example in this case:
```
gabriel@gabriel-laptop:~$ wget http://epsapublishing.com/index.php?modulo=obras&accion=obras_pop_up_descarga&idobras=1300&tipo=partitura&archivo=radaelli/RADAELLI_ZambadeTilo_Quarteto.pdf
[1] 9001
[2] 9002
[3] 9003
[4] 9004
[2]   Done                    accion=obras_pop_up_descarga
[3]   Done                    idobras=1300
[4]+  Done                    tipo=partitura
gabriel@gabriel-laptop:~$ --2009-01-26 08:31:09--  http://epsapublishing.com/index.php?modulo=obras
Resolving epsapublishing.com... 74.86.199.93
Connecting to epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.php?modulo=obras.1'

    [ <=>                                   ] 187         --.-K/s   in 0s      

2009-01-26 08:31:10 (12.9 MB/s) - `index.php?modulo=obras.1' saved [187]


[1]+  Done                    wget http://epsapublishing.com/index.php?modulo=obras

```

Why does wget ignore these files, while it actually should download them?

---

