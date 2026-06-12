---
title: "rythmbox in conky"
date: 2009-02-03
forum: General Help
---

### Post by S0m3th1ngw13rd on 2009-02-03
When I start conky rythmbox also starts with it is there a way to change conkyrc so the media player doesn't start with it. I still want it to display :::NOW PLAYING::: if is playing a song

here is code from cronky concerning rythmbox

```
${color green}${alignc}:::NOW PLAYING :::
${if_running rhythmbox}${color green}Artist: ${color green}${goto 50} ${exec rhythmbox-client --no-start --print-playing-format %ta}
${color green}Title: ${color green}${goto 50} ${exec rhythmbox-client --print-playing-format %tt}
${color green}Album: ${color green}${goto 50} ${exec rhythmbox-client --no-start --print-playing-format %at}
${color green}Genre: ${color green} ${goto 50} ${exec rhythmbox-client --no-start --print-playing-format %ag}${goto 130}   ${color green}Year: ${color green} ${exec rhythmbox-client --no-start --print-playing-format %ay}
${color green}Position: ${color green} ${exec rhythmbox-client --no-start --print-playing-format %te}${goto 130}       ${color green}Length: ${color green} ${exec rhythmbox-client --no-start --print-playing-format %td}${color green}$else${color green}${alignc}${font sans:size=6:bold}No Activity${font}$endif
```

or is there a better way?

---

### Post by m_duck on 2009-02-03
It looks like you are just missing the [COLOR=Red]--no-start[/COLOR] in line 3 above (the Title line). I think that should fix it.

---

### Post by S0m3th1ngw13rd on 2009-02-03
Good eye, that fixed it thank you

---

