---
title: "How to change regional settings (decimal, date, etc.)"
date: 2009-04-05
forum: General Help
---

### Post by notbitmonk on 2009-04-05
I have 8.10 and 8.04.  The 8.04 computer I have is in Spanish however I would like that decimals are displayed with a . instead of a , but do not know where to change it.  By doing some search there is supposed to be a Regional and Language menu under System - Administration but that option doesn't appear on my systems (only Language).  I also looked under Synaptic for some package but was unable to find something that looked like what I wanted.  Can anybody tell me what can I do?  TIA

---

### Post by notbitmonk on 2009-04-05
Bump

---

### Post by notbitmonk on 2009-04-05
I found a way around.  It is not a true workaround for me because I think that there should be a GUI or command line interface to it that provides better fine tuning (customization).  Ubuntu was installed in Spanish by Dell but it defaulted to Spain instead of Puerto Rico (even though I bought from the Puerto Rico store and upon installation selected Puerto Rico).  If you browse to /usr/share/i18n/locales and select es_PR (or any file for that matter) you will observe an unfriendly file because you can not make out what the settings should be.  Anyways, I tried changing some of the codes by hand by figuring out what was what (specifically the . and ,).  After restarting, the settings were not applied (either I did something wrong or there are some settings that take precedence).
I opened the environment document in /etc from the terminal by typing:
```
sudo gedit /etc/environment
```
and added the locale settings for the US
```

LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"

```
I did not change every locale aspect because not everything needed to be changed.  Just in case, these are the variables explanation from ```
man locale
```
[LIST]
[*]LC_CTYPE = Character classification and case conversion.
[*]LC_COLLATE = Collation order.
[*]LC_TIME = Date and time formats.
[*]LC_NUMERIC = Non-monetary numeric formats.
[*]LC_MONETARY = Monetary formats.
[*]LC_MESSAGES = Formats of informative and diagnostic messages and interactive responses.
[*]LC_PAPER = Paper size.
[/LIST]
As I said before, this is not a true solution because I just selected another locale instead of being able to edit the default one.  Furthermore, I do not know how to make the changes default so that if I add another user, it will inherit the customized settings.  I will mark it as solved but will keep on looking for a better solution and post accordingly.

---

### Post by SR_ELPIRATA on 2009-04-24
Que casualidad boricua :P

Entiendo el problema que tienes pero no se mucho de Ubuntu como para decirte que hacer, y si se puede o no. Yo uso el sistema mayormente en ingles pero estoy haciendo unas pruebas en español para ver como interactua con el lector de pantalla ORCA (Trabajo con muchos clientes ciegos).

No se si alguna vez has hecho la instalacion de Ubuntu por ti mismo, como dices, comprastes una Dell con Ubuntu pre-instalado. En las versiones en ingles que tengo, como he hecho la instalacion yo mismo, siempre especifico (que es el primer paso de la instalacion sino recuerdo mal) Puerto Rico.

Despues es que el sistema pregunta que tipo de teclado tengo (layout) y que idioma quiero el sistema que use. La unica vez que lo instale en español no recuerdo haberme fijado en el setting que tiene para los decimales, pero por lo que indicas, la coma se usa en españa para los decimales y aqui usamos el punto. Si no tienes data critica instalada y te atreves, te sugeriria que instalaras Ubuntu tu mismo, deberias notar la diferencia al menos en ese aspecto.

ELP

---

### Post by notbitmonk on 2009-05-11
Bueno compay, agradable saber que existen otros boricuas aquí.  He instalado y borrado Ubuntu desde 6.06 en mi computadora, siempre en inglés gringo pero esta vez le compré una computadora a la nena y me di con este problema.  Terminé reinstalando el sistema y ahora me funcionó.  Aún así es un problema no tener o saber donde cambiar estos settings.  Sigo chequiando y posteo si encuentro algo.

---

### Post by SR_ELPIRATA on 2009-05-11
Si, lo que pasa es que DELL, como dices, la instalo de fabrica en español pero el del otro lado del charco. Yo hasta ahora no me he topado con este problema pues principalmente la tengo en ingles y lo que si tengo es el keyboard layout switcher, para cuando necesito la ñ o los acentos. El asunto de los decimales no me aplica pues el sistema es en ingles y en USA se usan decimales con punto, como quieres para tu nena.

En España sí se usan los decimales con coma. Reinstalando el sistema, creo, es la forma mas facil de resolverlo.

---

### Post by theozzlives on 2009-05-11
This is an English speaking forum!

---

### Post by notbitmonk on 2009-05-12
You are absolutely right, sorry about it.  A quick summary of the above.  I bought a Dell Ubuntu system in Spanish and it looks like it Dell defaulted it for Spain Spanish and locale settings (I selected Puerto Rico in the country selection map).  Basically what this means is that decimals use a comma (,) instead of a dot (.).  In Puerto Rico we follow US customs (eventhough that means using the not so friendly Imperial measuring system) and that's why i wanted to change some locale parameters.  However, I decided to reinstall after copying the recovery DVD ISO that Dell provides.  I do not think that I did anything different from the first installation but it worked right this time.  Having said that, if anyone knows how to change the locale settings (through a GUI if possible) please let me know.

---

### Post by SR_ELPIRATA on 2009-05-13
He said this in english 3 posts above and not even you bothered to answer and now you get mad because we talked a bit of spanish?

---

### Post by dandnsmith on 2009-05-13
I've seen this sort of parochialism before (on other fora) _ I don't even remember anything saying this was english language only.

I'd love my spanish (and other languages) to be good enough to reply in the appropriate 'lingua franca'.

Later: found the bit which says posts should be in english - right in the middle of a lot of text. I wonder how many read all of this before posting.

---

### Post by SR_ELPIRATA on 2009-05-14
Oh I knew it was there, but since the problem had been described in english and nobody cared to answer I decided to go spaniard and have some fun with it.

---

