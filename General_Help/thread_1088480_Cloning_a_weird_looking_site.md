---
title: "Cloning a weird looking site"
date: 2009-03-06
forum: General Help
---

### Post by GabrielWolff on 2009-03-06
Or maybe not so weird, just I don't understand it...
There is a site offering sheet music. I would like to find a way to copy all of the sheet music offered.
1) The site is: ```
http://www.epsapublishing.com/
```
2) When downloading a file in the browser, I am sent to a URL that looks as follows: ```
http://www.epsapublishing.com/#6
``` and then:
3) The final download link looks like this: ```
http://www.epsapublishing.com/index.php?modulo=obras&accion=obras_pop_up_descarga&idobras=784&tipo=partitura&archivo=senanes/SENANES_TangoFor4Strings_DIF.pdf
```
4) Trying to use wget results in this: ```
gabriel@gabriel-laptop:~$ wget -r http://www.epsapublishing.com/--2009-03-06 10:04:30--  http://www.epsapublishing.com/
Resolving www.epsapublishing.com... 74.86.199.93
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.epsapublishing.com/index.html'

    [  <=>                                  ] 30,767      83.9K/s   in 0.4s    

2009-03-06 10:04:31 (83.9 KB/s) - `www.epsapublishing.com/index.html' saved [30767]

Loading robots.txt; please ignore errors.
--2009-03-06 10:04:31--  http://www.epsapublishing.com/robots.txt
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-06 10:04:31 ERROR 404: Not Found.

--2009-03-06 10:04:31--  http://www.epsapublishing.com/css/general.css
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17346 (17K) [text/css]
Saving to: `www.epsapublishing.com/css/general.css'

100%[======================================>] 17,346      70.8K/s   in 0.2s    

2009-03-06 10:04:32 (70.8 KB/s) - `www.epsapublishing.com/css/general.css' saved [17346/17346]

--2009-03-06 10:04:32--  http://www.epsapublishing.com/js/lib/scriptaculous/prototype.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 96066 (94K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/scriptaculous/prototype.js'

100%[======================================>] 96,066       204K/s   in 0.5s    

2009-03-06 10:04:32 (204 KB/s) - `www.epsapublishing.com/js/lib/scriptaculous/prototype.js' saved [96066/96066]

--2009-03-06 10:04:32--  http://www.epsapublishing.com/js/funciones/navegar.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 16578 (16K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/navegar.js'

100%[======================================>] 16,578      --.-K/s   in 0.001s  

2009-03-06 10:04:33 (25.7 MB/s) - `www.epsapublishing.com/js/funciones/navegar.js' saved [16578/16578]

--2009-03-06 10:04:33--  http://www.epsapublishing.com/includes/mm_menu.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 30389 (30K) [application/x-javascript]
Saving to: `www.epsapublishing.com/includes/mm_menu.js'

100%[======================================>] 30,389      --.-K/s   in 0.002s  

2009-03-06 10:04:33 (17.1 MB/s) - `www.epsapublishing.com/includes/mm_menu.js' saved [30389/30389]

--2009-03-06 10:04:33--  http://www.epsapublishing.com/js/funciones/menu.php
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.epsapublishing.com/js/funciones/menu.php'

    [  <=>                                  ] 30,468       124K/s   in 0.2s    

2009-03-06 10:04:33 (124 KB/s) - `www.epsapublishing.com/js/funciones/menu.php' saved [30468]

--2009-03-06 10:04:33--  http://www.epsapublishing.com/js/funciones/macromedia.js
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2260 (2.2K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/macromedia.js'

100%[======================================>] 2,260       --.-K/s   in 0s      

2009-03-06 10:04:34 (131 MB/s) - `www.epsapublishing.com/js/funciones/macromedia.js' saved [2260/2260]

--2009-03-06 10:04:34--  http://www.epsapublishing.com/js/funciones/base64.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1596 (1.6K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/base64.js'

100%[======================================>] 1,596       --.-K/s   in 0s      

2009-03-06 10:04:34 (103 MB/s) - `www.epsapublishing.com/js/funciones/base64.js' saved [1596/1596]

--2009-03-06 10:04:34--  http://www.epsapublishing.com/js/lib/scroller/scroller.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 10420 (10K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/scroller/scroller.js'

100%[======================================>] 10,420      65.4K/s   in 0.2s    

2009-03-06 10:04:34 (65.4 KB/s) - `www.epsapublishing.com/js/lib/scroller/scroller.js' saved [10420/10420]

--2009-03-06 10:04:34--  http://www.epsapublishing.com/includes/validar.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 380 [application/x-javascript]
Saving to: `www.epsapublishing.com/includes/validar.js'

100%[======================================>] 380         --.-K/s   in 0s      

2009-03-06 10:04:34 (27.3 MB/s) - `www.epsapublishing.com/includes/validar.js' saved [380/380]

--2009-03-06 10:04:34--  http://www.epsapublishing.com/js/modulos/index.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 404 Not Found
2009-03-06 10:04:34 ERROR 404: Not Found.

--2009-03-06 10:04:34--  http://www.epsapublishing.com/js/lib/rsh/rsh.compressed.js
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24437 (24K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/rsh/rsh.compressed.js'

100%[======================================>] 24,437      63.3K/s   in 0.4s    

2009-03-06 10:04:35 (63.3 KB/s) - `www.epsapublishing.com/js/lib/rsh/rsh.compressed.js' saved [24437/24437]

--2009-03-06 10:04:35--  http://www.epsapublishing.com/images/sombra_esq_izq.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 191 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_izq.gif'

100%[======================================>] 191         --.-K/s   in 0s      

2009-03-06 10:04:35 (13.8 MB/s) - `www.epsapublishing.com/images/sombra_esq_izq.gif' saved [191/191]

--2009-03-06 10:04:35--  http://www.epsapublishing.com/images/sombra_esq_der.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 127 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_der.gif'

100%[======================================>] 127         --.-K/s   in 0s      

2009-03-06 10:04:35 (9.48 MB/s) - `www.epsapublishing.com/images/sombra_esq_der.gif' saved [127/127]

--2009-03-06 10:04:35--  http://www.epsapublishing.com/images/logo_epsa_internas.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 2462 (2.4K) [image/gif]
Saving to: `www.epsapublishing.com/images/logo_epsa_internas.gif'

100%[======================================>] 2,462       --.-K/s   in 0s      

2009-03-06 10:04:35 (147 MB/s) - `www.epsapublishing.com/images/logo_epsa_internas.gif' saved [2462/2462]

--2009-03-06 10:04:35--  http://www.epsapublishing.com/images/usuario.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 260 [image/gif]
Saving to: `www.epsapublishing.com/images/usuario.gif'

100%[======================================>] 260         --.-K/s   in 0s      

2009-03-06 10:04:35 (18.9 MB/s) - `www.epsapublishing.com/images/usuario.gif' saved [260/260]

--2009-03-06 10:04:35--  http://www.epsapublishing.com/images/clave.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 206 [image/gif]
Saving to: `www.epsapublishing.com/images/clave.gif'

100%[======================================>] 206         --.-K/s   in 0s      

2009-03-06 10:04:36 (15.2 MB/s) - `www.epsapublishing.com/images/clave.gif' saved [206/206]

--2009-03-06 10:04:36--  http://www.epsapublishing.com/images/bt_flechi_azul_login.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 291 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_flechi_azul_login.gif'

100%[======================================>] 291         --.-K/s   in 0s      

2009-03-06 10:04:36 (21.4 MB/s) - `www.epsapublishing.com/images/bt_flechi_azul_login.gif' saved [291/291]

--2009-03-06 10:04:36--  http://www.epsapublishing.com/images/bt_olvido_clave.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 121 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_olvido_clave.gif'

100%[======================================>] 121         --.-K/s   in 0s      

2009-03-06 10:04:36 (9.18 MB/s) - `www.epsapublishing.com/images/bt_olvido_clave.gif' saved [121/121]

--2009-03-06 10:04:36--  http://www.epsapublishing.com/images/c_botonR.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 283 [image/gif]
Saving to: `www.epsapublishing.com/images/c_botonR.gif'

100%[======================================>] 283         --.-K/s   in 0s      

2009-03-06 10:04:36 (22.2 MB/s) - `www.epsapublishing.com/images/c_botonR.gif' saved [283/283]

--2009-03-06 10:04:36--  http://www.epsapublishing.com/swf/top_internas2.swf
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 27408 (27K) [application/x-shockwave-flash]
Saving to: `www.epsapublishing.com/swf/top_internas2.swf'

100%[======================================>] 27,408      73.1K/s   in 0.4s    

2009-03-06 10:04:36 (73.1 KB/s) - `www.epsapublishing.com/swf/top_internas2.swf' saved [27408/27408]

--2009-03-06 10:04:36--  http://www.epsapublishing.com/images/bt_mapa_sitio.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 217 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_mapa_sitio.gif'

100%[======================================>] 217         --.-K/s   in 0s      

2009-03-06 10:04:37 (15.3 MB/s) - `www.epsapublishing.com/images/bt_mapa_sitio.gif' saved [217/217]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/bt_pag_inicio.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 216 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_pag_inicio.gif'

100%[======================================>] 216         --.-K/s   in 0s      

2009-03-06 10:04:37 (15.9 MB/s) - `www.epsapublishing.com/images/bt_pag_inicio.gif' saved [216/216]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/bt_agregar_fav.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 181 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_agregar_fav.gif'

100%[======================================>] 181         --.-K/s   in 0s      

2009-03-06 10:04:37 (14.0 MB/s) - `www.epsapublishing.com/images/bt_agregar_fav.gif' saved [181/181]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/bt_faq.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 88 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_faq.gif'

100%[======================================>] 88          --.-K/s   in 0s      

2009-03-06 10:04:37 (6.36 MB/s) - `www.epsapublishing.com/images/bt_faq.gif' saved [88/88]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/bt_generoo.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 244 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_generoo.gif'

100%[======================================>] 244         --.-K/s   in 0s      

2009-03-06 10:04:37 (15.4 MB/s) - `www.epsapublishing.com/images/bt_generoo.gif' saved [244/244]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/nada.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 43 [image/gif]
Saving to: `www.epsapublishing.com/images/nada.gif'

100%[======================================>] 43          --.-K/s   in 0s      

2009-03-06 10:04:37 (3.00 MB/s) - `www.epsapublishing.com/images/nada.gif' saved [43/43]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/sombra_esq_abajo.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 103 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_abajo.gif'

100%[======================================>] 103         --.-K/s   in 0s      

2009-03-06 10:04:37 (7.56 MB/s) - `www.epsapublishing.com/images/sombra_esq_abajo.gif' saved [103/103]

--2009-03-06 10:04:37--  http://www.epsapublishing.com/images/logo_wm.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1070 (1.0K) [image/gif]
Saving to: `www.epsapublishing.com/images/logo_wm.gif'

100%[======================================>] 1,070       --.-K/s   in 0s      

2009-03-06 10:04:38 (72.7 MB/s) - `www.epsapublishing.com/images/logo_wm.gif' saved [1070/1070]

FINISHED --2009-03-06 10:04:38--
Downloaded: 28 files, 287K in 2.2s (131 KB/s)
gabriel@gabriel-laptop:~$
``` None of the scores are downloaded.

How do I get past this? The scores are for free, but downloading them one by one would take *years*!

---

### Post by dzark on 2009-03-06
can't download due to a login, where i dont speak enough of the language to get by the registraton... can you fill us out a username/password combo pls?

---

### Post by GabrielWolff on 2009-03-06
> **dzark said:**
> can't download due to a login, where i dont speak enough of the language to get by the registraton... can you fill us out a username/password combo pls?

Not sure what you mean by "username/password combo", but yes, I log in with some username and password. Is there a possibility to fill them in in wget?

EDIT: Tried it with username and password, same result:```
gabriel@gabriel-laptop:~$ wget -r http://gabrielwolff:XXPASSWORDXX@www.epsapublishing.com/
--2009-03-06 10:19:46--  http://gabrielwolff:*password*@www.epsapublishing.com/
Resolving www.epsapublishing.com... 74.86.199.93
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.epsapublishing.com/index.html'

    [  <=>                                  ] 30,767      81.4K/s   in 0.4s    

2009-03-06 10:19:47 (81.4 KB/s) - `www.epsapublishing.com/index.html' saved [30767]

Loading robots.txt; please ignore errors.
--2009-03-06 10:19:47--  http://gabrielwolff:*password*@www.epsapublishing.com/robots.txt
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-06 10:19:47 ERROR 404: Not Found.

--2009-03-06 10:19:47--  http://gabrielwolff:*password*@www.epsapublishing.com/css/general.css
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17346 (17K) [text/css]
Saving to: `www.epsapublishing.com/css/general.css'

100%[======================================>] 17,346      67.5K/s   in 0.3s    

2009-03-06 10:19:48 (67.5 KB/s) - `www.epsapublishing.com/css/general.css' saved [17346/17346]

--2009-03-06 10:19:48--  http://gabrielwolff:*password*@www.epsapublishing.com/js/lib/scriptaculous/prototype.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 96066 (94K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/scriptaculous/prototype.js'

100%[======================================>] 96,066       187K/s   in 0.5s    

2009-03-06 10:19:48 (187 KB/s) - `www.epsapublishing.com/js/lib/scriptaculous/prototype.js' saved [96066/96066]

--2009-03-06 10:19:48--  http://gabrielwolff:*password*@www.epsapublishing.com/js/funciones/navegar.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 16578 (16K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/navegar.js'

100%[======================================>] 16,578      --.-K/s   in 0.001s  

2009-03-06 10:19:49 (18.3 MB/s) - `www.epsapublishing.com/js/funciones/navegar.js' saved [16578/16578]

--2009-03-06 10:19:49--  http://gabrielwolff:*password*@www.epsapublishing.com/includes/mm_menu.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 30389 (30K) [application/x-javascript]
Saving to: `www.epsapublishing.com/includes/mm_menu.js'

100%[======================================>] 30,389      --.-K/s   in 0.002s  

2009-03-06 10:19:49 (14.2 MB/s) - `www.epsapublishing.com/includes/mm_menu.js' saved [30389/30389]

--2009-03-06 10:19:49--  http://gabrielwolff:*password*@www.epsapublishing.com/js/funciones/menu.php
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.epsapublishing.com/js/funciones/menu.php'

    [ <=>                                   ] 30,468      --.-K/s   in 0.1s    

2009-03-06 10:19:49 (235 KB/s) - `www.epsapublishing.com/js/funciones/menu.php' saved [30468]

--2009-03-06 10:19:49--  http://gabrielwolff:*password*@www.epsapublishing.com/js/funciones/macromedia.js
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2260 (2.2K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/macromedia.js'

100%[======================================>] 2,260       --.-K/s   in 0s      

2009-03-06 10:19:49 (138 MB/s) - `www.epsapublishing.com/js/funciones/macromedia.js' saved [2260/2260]

--2009-03-06 10:19:49--  http://gabrielwolff:*password*@www.epsapublishing.com/js/funciones/base64.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1596 (1.6K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/funciones/base64.js'

100%[======================================>] 1,596       --.-K/s   in 0s      

2009-03-06 10:19:49 (101 MB/s) - `www.epsapublishing.com/js/funciones/base64.js' saved [1596/1596]

--2009-03-06 10:19:49--  http://gabrielwolff:*password*@www.epsapublishing.com/js/lib/scroller/scroller.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 10420 (10K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/scroller/scroller.js'

100%[======================================>] 10,420      61.3K/s   in 0.2s    

2009-03-06 10:19:50 (61.3 KB/s) - `www.epsapublishing.com/js/lib/scroller/scroller.js' saved [10420/10420]

--2009-03-06 10:19:50--  http://gabrielwolff:*password*@www.epsapublishing.com/includes/validar.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 380 [application/x-javascript]
Saving to: `www.epsapublishing.com/includes/validar.js'

100%[======================================>] 380         --.-K/s   in 0s      

2009-03-06 10:19:50 (30.2 MB/s) - `www.epsapublishing.com/includes/validar.js' saved [380/380]

--2009-03-06 10:19:50--  http://gabrielwolff:*password*@www.epsapublishing.com/js/modulos/index.js
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 404 Not Found
2009-03-06 10:19:50 ERROR 404: Not Found.

--2009-03-06 10:19:50--  http://gabrielwolff:*password*@www.epsapublishing.com/js/lib/rsh/rsh.compressed.js
Connecting to www.epsapublishing.com|74.86.199.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24437 (24K) [application/x-javascript]
Saving to: `www.epsapublishing.com/js/lib/rsh/rsh.compressed.js'

100%[======================================>] 24,437      62.4K/s   in 0.4s    

2009-03-06 10:19:51 (62.4 KB/s) - `www.epsapublishing.com/js/lib/rsh/rsh.compressed.js' saved [24437/24437]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/sombra_esq_izq.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 191 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_izq.gif'

100%[======================================>] 191         --.-K/s   in 0s      

2009-03-06 10:19:51 (14.9 MB/s) - `www.epsapublishing.com/images/sombra_esq_izq.gif' saved [191/191]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/sombra_esq_der.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 127 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_der.gif'

100%[======================================>] 127         --.-K/s   in 0s      

2009-03-06 10:19:51 (9.97 MB/s) - `www.epsapublishing.com/images/sombra_esq_der.gif' saved [127/127]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/logo_epsa_internas.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 2462 (2.4K) [image/gif]
Saving to: `www.epsapublishing.com/images/logo_epsa_internas.gif'

100%[======================================>] 2,462       --.-K/s   in 0s      

2009-03-06 10:19:51 (144 MB/s) - `www.epsapublishing.com/images/logo_epsa_internas.gif' saved [2462/2462]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/usuario.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 260 [image/gif]
Saving to: `www.epsapublishing.com/images/usuario.gif'

100%[======================================>] 260         --.-K/s   in 0s      

2009-03-06 10:19:51 (19.1 MB/s) - `www.epsapublishing.com/images/usuario.gif' saved [260/260]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/clave.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 206 [image/gif]
Saving to: `www.epsapublishing.com/images/clave.gif'

100%[======================================>] 206         --.-K/s   in 0s      

2009-03-06 10:19:51 (15.3 MB/s) - `www.epsapublishing.com/images/clave.gif' saved [206/206]

--2009-03-06 10:19:51--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_flechi_azul_login.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 291 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_flechi_azul_login.gif'

100%[======================================>] 291         --.-K/s   in 0s      

2009-03-06 10:19:52 (34.6 MB/s) - `www.epsapublishing.com/images/bt_flechi_azul_login.gif' saved [291/291]

--2009-03-06 10:19:52--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_olvido_clave.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 121 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_olvido_clave.gif'

100%[======================================>] 121         --.-K/s   in 0s      

2009-03-06 10:19:52 (9.66 MB/s) - `www.epsapublishing.com/images/bt_olvido_clave.gif' saved [121/121]

--2009-03-06 10:19:52--  http://gabrielwolff:*password*@www.epsapublishing.com/images/c_botonR.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 283 [image/gif]
Saving to: `www.epsapublishing.com/images/c_botonR.gif'

100%[======================================>] 283         --.-K/s   in 0s      

2009-03-06 10:19:52 (21.4 MB/s) - `www.epsapublishing.com/images/c_botonR.gif' saved [283/283]

--2009-03-06 10:19:52--  http://gabrielwolff:*password*@www.epsapublishing.com/swf/top_internas2.swf
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 27408 (27K) [application/x-shockwave-flash]
Saving to: `www.epsapublishing.com/swf/top_internas2.swf'

100%[======================================>] 27,408       105K/s   in 0.3s    

2009-03-06 10:19:52 (105 KB/s) - `www.epsapublishing.com/swf/top_internas2.swf' saved [27408/27408]

--2009-03-06 10:19:52--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_mapa_sitio.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 217 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_mapa_sitio.gif'

100%[======================================>] 217         --.-K/s   in 0s      

2009-03-06 10:19:52 (17.5 MB/s) - `www.epsapublishing.com/images/bt_mapa_sitio.gif' saved [217/217]

--2009-03-06 10:19:52--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_pag_inicio.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 216 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_pag_inicio.gif'

100%[======================================>] 216         --.-K/s   in 0s      

2009-03-06 10:19:53 (16.4 MB/s) - `www.epsapublishing.com/images/bt_pag_inicio.gif' saved [216/216]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_agregar_fav.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 181 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_agregar_fav.gif'

100%[======================================>] 181         --.-K/s   in 0s      

2009-03-06 10:19:53 (13.9 MB/s) - `www.epsapublishing.com/images/bt_agregar_fav.gif' saved [181/181]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_faq.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 88 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_faq.gif'

100%[======================================>] 88          --.-K/s   in 0s      

2009-03-06 10:19:53 (6.99 MB/s) - `www.epsapublishing.com/images/bt_faq.gif' saved [88/88]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/bt_generoo.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 244 [image/gif]
Saving to: `www.epsapublishing.com/images/bt_generoo.gif'

100%[======================================>] 244         --.-K/s   in 0s      

2009-03-06 10:19:53 (19.3 MB/s) - `www.epsapublishing.com/images/bt_generoo.gif' saved [244/244]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/nada.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 43 [image/gif]
Saving to: `www.epsapublishing.com/images/nada.gif'

100%[======================================>] 43          --.-K/s   in 0s      

2009-03-06 10:19:53 (3.03 MB/s) - `www.epsapublishing.com/images/nada.gif' saved [43/43]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/sombra_esq_abajo.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 103 [image/gif]
Saving to: `www.epsapublishing.com/images/sombra_esq_abajo.gif'

100%[======================================>] 103         --.-K/s   in 0s      

2009-03-06 10:19:53 (8.52 MB/s) - `www.epsapublishing.com/images/sombra_esq_abajo.gif' saved [103/103]

--2009-03-06 10:19:53--  http://gabrielwolff:*password*@www.epsapublishing.com/images/logo_wm.gif
Reusing existing connection to www.epsapublishing.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1070 (1.0K) [image/gif]
Saving to: `www.epsapublishing.com/images/logo_wm.gif'

100%[======================================>] 1,070       --.-K/s   in 0s      

2009-03-06 10:19:53 (79.0 MB/s) - `www.epsapublishing.com/images/logo_wm.gif' saved [1070/1070]

FINISHED --2009-03-06 10:19:53--
Downloaded: 28 files, 287K in 2.1s (140 KB/s)
gabriel@gabriel-laptop:~$ 

```

---

### Post by dzark on 2009-03-06
that'd be exactly what i mean by a 'username/password combo' 

After a quick google translation of thier terms and conditions, i came across a line stating:

"Not be reproduced and / or commercialization of all or part of any service or content of the Website .- "

"A fin de evitar cualquier duda al respecto, nada de lo establecido en el Sitio Web podrá ser considerado como una autorización, licencia, venta, transmisión o cesión de derechos a favor del Usuario. En tal sentido, se deja expresamente establecido que se encuentra absolutamente prohibida la inclusión o sincronización de las obras musicales del catálogo de la Editorial con cualquier otra obra o contenido, sin contar con el previo y expreso consentimiento de la Editorial y/o de quien legalmente corresponda.-"

That pretty much closes this thread.

---

### Post by GabrielWolff on 2009-03-06
> **dzark said:**
> that'd be exactly what i mean by a 'username/password combo' 

After a quick google translation of thier terms and conditions, i came across a line stating:

"Not be reproduced and / or commercialization of all or part of any service or content of the Website .- "

"A fin de evitar cualquier duda al respecto, nada de lo establecido en el Sitio Web podrá ser considerado como una autorización, licencia, venta, transmisión o cesión de derechos a favor del Usuario. En tal sentido, se deja expresamente establecido que se encuentra absolutamente prohibida la inclusión o sincronización de las obras musicales del catálogo de la Editorial con cualquier otra obra o contenido, sin contar con el previo y expreso consentimiento de la Editorial y/o de quien legalmente corresponda.-"

That pretty much closes this thread.

Sorry, I think I need a transation into simple terms. The website offers the scores for free download, so how come it's forbidden at the same time...?

---

### Post by dzark on 2009-03-06
taking what you need is okay, taking everything isn't. dont be greedy :P

---

### Post by GabrielWolff on 2009-03-06
> **dzark said:**
> taking what you need is okay, taking everything isn't. dont be greedy :P
I'm not greedy, I'm... thoroughgoing ;)

---

