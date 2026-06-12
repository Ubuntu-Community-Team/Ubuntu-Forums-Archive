---
title: "Wireless not working on vostro 1310"
date: 2010-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gcmarimon on 2010-04-23
Hey ppl, how you doing ?
im asking help because ive reinstalled several times ( 4 or more) ubuntu O.S. and still dont get the wireless to work... i had to format the laptop to remove windows definitely....
now i cant manage my wireless to work... the signal simbol which shows the signal strength still shows at the top bar, but when i click it to show the available wireless connections it does not show any...
just sopme vpn conection i can configure...
if type #ifconfig 

eth0      Link encap:Ethernet  Endereço de HW 00:21:70:fa:9f:93   
           UP BROADCAST MULTICAST  MTU:1500  Métrica:1  
           pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0  
           Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0  
           colisões:0 txqueuelen:1000  
           RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)  
           IRQ:30 Endereço de E/S:0x8000  
 

 lo        Link encap:Loopback Local   
           inet end.: 127.0.0.1  Masc:255.0.0.0  
           endereço inet6: ::1/128 Escopo:Máquina  
           UP LOOPBACK RUNNING  MTU:16436  Métrica:1  
           pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0  
           Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0  
           colisões:0 txqueuelen:0  
           RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)  
 



now ive conected via wire and have downloaded the suggested drivers for nvidia graphical card and for broadcom wireless card.... but the wireless card stil does not work....

please help me assap!i realy need it to work!

thanks a lot
regards!

---

### Post by mikewhatever on 2010-04-23
And the model of the Broadcom card is ...?
If not sure, post the output of *lspci -v | grep -i broadcom*.

---

### Post by geniusguy2000 on 2010-04-24
I had the same problem I just sent it back.

---

