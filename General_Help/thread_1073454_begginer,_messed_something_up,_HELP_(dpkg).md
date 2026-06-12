---
title: "begginer, messed something up, HELP (dpkg)"
date: 2009-02-18
forum: General Help
---

### Post by nickmatteis on 2009-02-18
hi, i literally installed ubuntu intrepid ibex 2 days ago as a boot camp partition on my mac book surprisingly my broadcom wireless chip works,but thats not my problem.
being a total newbie, i searched google on how to install compiz fusion (cause really whats a linux machine without it) and i found a website (dont remeber what one) and it gave step by step codes for terminal on how to install the gnome desktop environment, or update it, im really not sure, so terminal was doing a whole long process, then i came across another site that said all i had to do was find compiz in the synaptic pakage manager, so i left the terminal open and opened the manager, "Error, you cannot blah blah blah while another process is running" so i just terminated the terminal, little did i know that it would mess up my "configuration defaults for GNOME power manager. so i cant install update, i cant even open the synaptic manager w/o an error message, but worst of all i cant install anything!!

in terminal i tried to install "yum" cause i read a thrad on how to re-install gnome (hoping that would be the solution) but terminal told me that 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

so i typed in the 'dpkg --configure -a' only to get another message

"nick@macbook:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege"

and as far as i know i dont have superuser privliges PLEASE HELP ME	](*,)	](*,)	](*,)

---

### Post by blackgr on 2009-02-18
You are just messing with all these commands thinking that things are broken. to gain these pleaviledges you have to do that
```

sudo dpkg-reconfigure -a

```
Compiz is installed by default. Just go System>Preferences>Appearence>Visual effects

---

### Post by nickmatteis on 2009-02-18
sorry i meant "Compiz-Fusion"

---

### Post by nickmatteis on 2009-02-18
i ran that code, it did everything fine but im still recieving the error message aout manually installing dpkg --configure -a

---

