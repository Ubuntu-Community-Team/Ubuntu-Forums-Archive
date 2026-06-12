---
title: "Usb inservible?"
date: 2008-03-10
forum: Catalan Team
---

### Post by raukonak on 2008-03-10
Hola a totom! tot bé? 

Tijnc un problema amb el mp3 d'una amiga. Suposo que el devia trure a lo bestia i ara no em funciona. Per si de cas, abans de donar-li l'ultim adeu em voldria assegurar i saber si algú d'aqui li ha passat alguna cosa semblant o si té alguna solució miraculosa. He intentat muntar-lo, però no m'ha deixat, desprès ho he fet amb el mount, però no em trobava el /dev/sdc, després he intentat formatejar-lo per si el sistema d'arxius estava corrupte, però el gparted no me'l trobava i ho he fet per la consola. He provat el mkfs.vfat amb un parell d'opcions que he trobat googlejant ( sudo mkfs.vfat -IF 32 /dev/sdc), amb el fdisk -l no em sortia res, os igui que no hi ha cap partició i despres li he donat un sfdisk -l /dev/sdc que no se que cony he fet però tampoc ha servit de gaire.


Us enganxo el dmesg, que em sembla que és el que més claretat pot oferir
(es repeteix tot una pila de vegades, però el poso tot que no sigui que em passi de llest i em deixi el més important):


<code>[ 3576.159840] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3576.159846] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3576.162393] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3576.162402] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3578.148698] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3578.148707] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3578.148715] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3578.152054] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3578.152060] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3578.152068] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3578.152075] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3578.153179] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3578.153184] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3578.156173] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3578.156177] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3578.156183] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3578.159420] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3578.159424] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3578.159430] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3578.159436] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3578.160546] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3578.160551] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3580.143563] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3580.143571] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3580.143578] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3580.146934] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3580.146939] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3580.146946] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3580.146953] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3580.148020] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3580.148025] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3580.150929] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3580.150933] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3580.150940] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3580.154177] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3580.154181] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3580.154188] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3580.154195] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3580.155303] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3580.155308] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3582.141692] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3582.141699] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3582.141707] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3582.145063] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3582.145068] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3582.145074] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3582.145081] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3582.146129] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3582.146134] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3582.149058] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3582.149062] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3582.149069] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3582.152306] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3582.152310] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3582.152317] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3582.152323] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3582.153432] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3582.153437] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3584.139821] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3584.139828] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3584.139836] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3584.143192] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3584.143197] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3584.143204] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3584.143210] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3584.144235] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3584.144240] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3584.147187] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3584.147191] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3584.147198] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3584.150435] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3584.150439] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3584.150446] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3584.150453] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3584.151561] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3584.151565] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3586.137825] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3586.137832] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3586.137840] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3586.141196] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3586.141201] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3586.141207] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3586.141215] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3586.142340] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3586.142346] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3586.145322] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3586.145330] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3586.145337] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3586.148564] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3586.148568] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3586.148576] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3586.148583] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3586.149691] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3586.149696] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3588.135954] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3588.135961] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3588.135969] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3588.139325] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3588.139329] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3588.139336] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3588.139343] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3588.140455] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3588.140461] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3588.143319] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3588.143324] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3588.143330] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3588.146568] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3588.146572] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3588.146579] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3588.146585] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3588.147694] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3588.147699] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3590.134083] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3590.134091] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3590.134099] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3590.137454] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3590.137459] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3590.137466] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3590.137473] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3590.138559] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3590.138564] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3590.141448] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3590.141452] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3590.141459] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3590.144696] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3590.144701] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3590.144707] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3590.144713] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3590.145822] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3590.145827] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3592.132212] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3592.132219] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3592.132228] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3592.135583] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3592.135588] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3592.135594] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3592.135601] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3592.136668] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3592.136673] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3592.139577] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3592.139581] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3592.139588] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3592.142826] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3592.142830] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3592.142837] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3592.142843] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3592.143951] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3592.143956] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3594.130342] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3594.130350] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3594.130358] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3594.133711] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3594.133716] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3594.133723] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3594.133731] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3594.134773] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3594.134779] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3594.137706] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3594.137710] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3594.137717] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3594.140954] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3594.140959] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3594.140965] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3594.140972] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3594.142081] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3594.142085] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3596.128469] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3596.128476] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3596.128484] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3596.131840] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3596.131845] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3596.131852] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3596.131859] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3596.132883] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3596.132888] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3596.135835] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3596.135839] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3596.135846] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3596.139083] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3596.139087] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3596.139094] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3596.139100] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3596.140209] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3596.140214] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3598.126473] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3598.126481] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3598.126489] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3598.129846] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3598.129853] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3598.129860] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3598.129866] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3598.130981] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3598.130988] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3598.133839] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3598.133844] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3598.133850] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3598.137087] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3598.137091] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3598.137097] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3598.137103] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3598.138214] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3598.138218] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3600.124602] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3600.124610] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3600.124617] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3600.127973] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3600.127977] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3600.127985] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3600.127992] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3600.129114] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3600.129120] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3600.131968] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3600.131972] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3600.131979] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3600.135216] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3600.135221] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3600.135228] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3600.135233] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3600.136342] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3600.136346] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3602.122731] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3602.122739] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3602.122747] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3602.126102] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3602.126107] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3602.126114] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3602.126121] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3602.127205] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3602.127210] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3602.130097] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3602.130101] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3602.130107] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3602.133345] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3602.133349] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3602.133355] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3602.133362] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3602.134471] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3602.134476] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3604.120860] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3604.120868] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3604.120876] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3604.124231] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3604.124236] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3604.124243] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3604.124250] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3604.125313] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3604.125318] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3604.128250] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3604.128260] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3604.128266] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3604.131477] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3604.131484] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3604.131491] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3604.131498] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3604.132647] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3604.132653] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3606.118989] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3606.118996] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3606.119004] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3606.122360] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3606.122364] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3606.122371] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3606.122378] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3606.123426] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3606.123432] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3606.126480] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3606.126484] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3606.126491] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3606.129852] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3606.129857] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3606.129862] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3606.129868] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3606.130978] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3606.130983] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3608.116993] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3608.117001] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3608.117009] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3608.120239] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3608.120244] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3608.120251] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3608.120258] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3608.121365] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3608.121370] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3608.124233] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3608.124238] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3608.124245] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3608.127482] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3608.127486] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3608.127492] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3608.127499] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3608.128608] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3608.128612] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3610.115247] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3610.115254] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3610.115262] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3610.118633] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3610.118641] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3610.118648] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3610.118653] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3610.119676] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3610.119682] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3610.122612] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3610.122617] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3610.122624] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3610.125861] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3610.125866] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3610.125873] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3610.125880] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3610.126987] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3610.126992] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3612.113250] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3612.113257] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3612.113266] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3612.116621] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3612.116626] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3612.116633] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3612.116641] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3612.117750] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3612.117755] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3612.120616] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3612.120620] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3612.120627] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3612.123864] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3612.123869] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3612.123875] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3612.123881] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3612.124991] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3612.124995] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3614.111379] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3614.111386] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3614.111394] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3614.114750] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3614.114755] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3614.114762] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3614.114769] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3614.115853] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3614.115859] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3614.118745] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3614.118749] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3614.118756] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3614.121993] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3614.121997] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3614.122004] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3614.122011] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3614.123119] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3614.123123] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3616.109508] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3616.109516] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3616.109523] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3616.112879] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3616.112884] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3616.112891] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3616.112898] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3616.113962] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3616.113967] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3616.116874] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3616.116878] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3616.116884] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3616.120122] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3616.120126] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3616.120133] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3616.120139] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3616.121248] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3616.121253] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3618.107511] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3618.107519] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3618.107527] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3618.110758] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3618.110763] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3618.110771] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3618.110777] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3618.111884] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3618.111889] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3618.114753] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3618.114757] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3618.114764] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3618.118001] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3618.118006] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3618.118012] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3618.118018] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3618.119128] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3618.119132] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3620.105765] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3620.105773] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3620.105781] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3620.109137] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3620.109141] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3620.109148] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3620.109155] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3620.110177] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3620.110182] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3620.113132] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3620.113136] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3620.113142] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3620.116380] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3620.116384] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3620.116390] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3620.116397] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3620.117507] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3620.117511] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3622.103770] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3622.103777] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3622.103785] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3622.107268] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3622.107273] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3622.107279] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3622.107285] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3622.108284] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3622.108289] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3622.111261] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3622.111265] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3622.111272] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3622.114509] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3622.114514] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3622.114520] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3622.114526] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3622.115635] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3622.115639] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3624.101898] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3624.101906] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3624.101914] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3624.105270] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3624.105274] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3624.105281] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3624.105288] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3624.106395] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3624.106400] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3624.109265] sd 4:0:0:0: [sdc] Unit Not Ready
[ 3624.109269] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3624.109275] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3624.112513] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3624.112517] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3624.112523] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 3624.112530] sd 4:0:0:0: [sdc] Add. Sense: Medium format corrupted
[ 3624.113639] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 3624.113644] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 3625.845542] usb 3-6: USB disconnect, address 4
[ 3632.138784] usb 3-6: new high speed USB device using ehci_hcd and address 5
[ 3632.271746] usb 3-6: configuration #1 chosen from 1 choice
[ 3632.272150] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3632.272256] usb-storage: device found at 5
[ 3632.272260] usb-storage: waiting for device to settle before scanning</code>

---

### Post by orestesmas on 2008-03-10
Jo els passos que has seguit els veig molt raonables.

És curiós perquè en aquesta tirallonga de missatges et va dient constantment "Unit not ready". Potser és que el *firmware* detecta un sistema de fitxers corrupte i triga molt a activar el senyal de "disponible". Fins que no estigui activat no podràs formatejar res.

Com tu dius, sembla que no hi ha una taula de particions definida. Aleshores cal formatejar el disc sencer (com si fos un disquet dels d'abans)

Torna-ho a provar, esperant una estona després de connectar-lo. L'opció -F permet escollir la mida de la FAT. Normalment escull automàticament entre una FAT de 12 bits o de 16. Si és de 32 li ho has d'indicar expressament. Jo de tu provaria amb les 3 opcions (especialment la de 16). De quants MB era aquest MP3?

També hi ha altres opcions (-S 512, er exemple). Mira't el manual i ves provant. No desesperis. És estrany que un trasto d'aquests deixi de funcionar només perquè el formategis...

---

