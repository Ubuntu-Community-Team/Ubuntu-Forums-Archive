---
title: "Star Wars games on Ubuntu"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Dev'olution on 2007-06-01
Hey,

I've been trying to install both Star Wars: Galactic Battlegrounds and Star Wars: Jedi Knight II: Jedi Outcast on my Ubuntu laptop, but unfortunately during both installs i get an 'Error 21'.

What is Error 21? And has anyone successfully installed either one of those games?

Thanks,
Kris

---

### Post by Ferrat on 2007-06-01
are you using the latest version of wine? 

cause Jedi Knight II : Jedi Outcast is rated platinum by most users = installs and playes without any problems at all (a.k.a. Out of the box)

[http://appdb.winehq.org/appview.php?iAppId=716](http://appdb.winehq.org/appview.php?iAppId=716)

Is it Star Wars : Battlegfront you mean ?

that one is rated as gold by many = works with just some small tweaking

[http://appdb.winehq.org/appview.php?iAppId=3007](http://appdb.winehq.org/appview.php?iAppId=3007)

Star Wars : Battlefront 2 however no one seem to have any luck with  

[http://appdb.winehq.org/appview.php?iAppId=3803](http://appdb.winehq.org/appview.php?iAppId=3803)

---

### Post by Dev'olution on 2007-06-01
Nah Star Wars: Galactic Battlegrounds Saga is a RTS game.

---

### Post by Dev'olution on 2007-06-01
The main part it's freezing up on is the damned installation.. thats where i get the error 21 at 76%... i also had the same problem with the Jedi Outcast cd at roughly 21%...

Please help?

---

### Post by Dev'olution on 2007-06-01
After even further investigation,

It seems as though it freezes when it asks for second cd. (Error 21)

---

### Post by Ferrat on 2007-06-01
Give this a try 

[http://www.liflg.org/?catid=7&gameid=45](http://www.liflg.org/?catid=7&gameid=45)

it's Loki Installers for Linux Games, it installs JKII:JO on wine, might be a bit old but worth a try 

if not, please post 
what version of wine you are using?
what the terminal says when it freezes?

---

### Post by Ferrat on 2007-06-01
if it freezes when looking for CD2 then try copying all CDs to a folder and installing from there

---

### Post by Dev'olution on 2007-06-01
> **Ferrat said:**
> Give this a try 

[http://www.liflg.org/?catid=7&gameid=45](http://www.liflg.org/?catid=7&gameid=45)

it's Loki Installers for Linux Games, it installs JKII:JO on wine, might be a bit old but worth a try 

if not, please post 
what version of wine you are using?
what the terminal says when it freezes?

I'm running 0.9.39

The terminal reads:

```
 err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {aa7e2066-cb55-11d2-8094-00104b1f9838}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {aa7e2066-cb55-11d2-8094-00104b1f9838}, 80040155
err:ole:_marshal_interface Marshalling interface {aa7e2066-cb55-11d2-8094-00104b1f9838} failed with 80040155
err:ole:xCall Failed to serialize param, hres 80040155
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:xCall RpcChannelBuffer SendReceive failed, 80004005
err:ole:marshal_object couldn't get IPSFactory buffer for interface {83755dd1-086b-11d3-8868-00c04f72f303}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002

```

---

### Post by Dev'olution on 2007-06-01
Any help guys with the SWGB game? Please?

---

### Post by lordhebe on 2007-06-01
> I'm running 0.9.39

Doesn't exist yet. On SWGB it seems as though it's been working for some time [http://appdb.winehq.org/appview.php?iVersionId=3757]("http://appdb.winehq.org/appview.php?iVersionId=3757") so I don't knoiw what to suggest. In winecfg  make sure that your drives are set up, and that drive D is configured as a cdrom drive.

---

### Post by Dev'olution on 2007-06-01
> **lordhebe said:**
> Doesn't exist yet. On SWGB it seems as though it's been working for some time [http://appdb.winehq.org/appview.php?iVersionId=3757]("http://appdb.winehq.org/appview.php?iVersionId=3757") so I don't knoiw what to suggest. In winecfg  make sure that your drives are set up, and that drive D is configured as a cdrom drive.

Ooops I meant 0.9.37

---

