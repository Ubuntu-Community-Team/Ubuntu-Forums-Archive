---
title: "Solución a instalación do Modem USB Huawei E1752 en Lucid"
date: 2010-06-03
forum: Galician LoCo Team
---

### Post by leillo1975 on 2010-06-03
Hola

No dia de hoxe pasaronme un modem USB de internet movil da marca Huawei E1752 dunha compañía que non vou a decir para non facer propaganda. O caso é que conectando directamente o modem o porto USB o Network Manager non detecta ningún dispositivo de rede deste tipo. Buscando información pola web o final conseguín a información necesaria para que isto deixase de ser un problema.

O primeiro que temos que instalar é o paquete &#8220;usb-modeswitch&#8221;:

```
sudo apt-get install usb-modeswitch
```

Logo conectaremos o modem USB e premeremos co botón dereito do rato no icono do Network Manager no panel superior do Escritorio de Ubuntu. Veremos que agora pon &#8220;Activar a Banda Larga Movil&#8221;, pois activamola, e logo damoslle da mesma forma a &#8220;Editar as conexións&#8221;. Prememos na pestana de &#8220;Banda larga movil&#8221; e engadimos unha nova conexión.  Si antes de instalar o paquete &#8220;usb-modeswitch&#8221; trataramos de facer isto, veriamos que no combo box donde se escolle o dispositivo a instalar non saia nada, e en troques agora sainos o modelo de modem. Agora so temos que seguir o asistente (escoller pais, compañía, etc) e no último paso por o PIN que nos facilitaron.

Xa temos lista a conexión, agora so temos que activala no Network Manager pinchando co boton Esquerdo na nova conexión que nos sai en &#8220;Banda Larga movil&#8221; e listo, a navegar.

Non o probei con outros modems de outras marcas e modelos, pero si non vos funciona o que tendes podedes probar. Estaría ben que comentarades se vos funciona ou non.

NOTA: Este post está tamén publicado no meu blogue (mirade firma)

---

### Post by pikamoku on 2010-06-10
grazas ;)

---

