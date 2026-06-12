---
title: "Alsa-utils problem"
date: 2009-03-10
forum: General Help
---

### Post by sprudhom2 on 2009-03-10
Hi I'm trying to compile alsa for my EMU-1616(PCMCIA/PCI adaptor) sound card. 
Ref website:
[http://forums.audiofanzine.com/index,idtopic,330002,mao,emu_1616m__adaptateur_pcmcia_expresscard__linux.html](http://forums.audiofanzine.com/index,idtopic,330002,mao,emu_1616m__adaptateur_pcmcia_expresscard__linux.html)
and
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

But when I try to do the third step (compile alsa-utils... I have this message...(How can I repair This)
***
Making all in include
make[1]: entrant dans le répertoire « /usr/src/alsa/alsa-utils-1.0.18/include »
make  all-am
make[2]: entrant dans le répertoire « /usr/src/alsa/alsa-utils-1.0.18/include »
make[2]: quittant le répertoire « /usr/src/alsa/alsa-utils-1.0.18/include »
make[1]: quittant le répertoire « /usr/src/alsa/alsa-utils-1.0.18/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl/init »
make[2]: entrant dans le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
    then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
    then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
    then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
utils.c: In function ‘initfailed’:
utils.c:92: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:93: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:94: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:95: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
    then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
init_parse.c: In function ‘parse_line’:
init_parse.c:1550: attention : ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
init_parse.c:1560: attention : ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc  -g -O2   -o alsactl  alsactl.o state.o utils.o init_parse.o  -lasound -lm -ldl -lpthread
xmlto man alsactl_init.xml
/bin/bash: xmlto : commande introuvable
make[2]: *** [alsactl_init.7] Erreur 127
make[2]: quittant le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /usr/src/alsa/alsa-utils-1.0.18/alsactl »
make: *** [all-recursive] Erreur 1
***

---

### Post by sprudhom2 on 2009-03-10
No idea

---

