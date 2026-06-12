---
title: "NAS for data storage"
date: 2009-01-20
forum: General Help
---

### Post by bonfire89 on 2009-01-20
Hey there,


I have a home server and I have a lot of data and it can be difficult to fit all the drives in, find slots on the mobo, add new controllers and all that jazz.

I was thinking, why not use a network card instead of a sata controller and have a NAS connected to the server directly with a crossover cable. I don't need the fast speeds anyways since this is all storage....


perhaps it might be better for me to just upgrade my "server" properly.


I really don't know. Something I just thought about. Till now I have always thought the home NAS systems were lame. I don't like how I can't have full control over them, but, if I attach them directly to the server and use the server as a gatekeeper of sorts for the NAS it would be okay.

Anyways.. any thoughts? thanks.

---

### Post by kaivalagi on 2009-01-20
There will obviously be an overhead...

Standard setup with Internal SATA:
SATA HDD -> SATA Controller -> System Bus

NAS based setup using SATA spec disks:
SATA HDD -> SATA Controller -> **Network Adapter ---> LAN ---> Network Adapter** -> System Bus

Transferring data across a network no matter how simple the network means creating packets containing a header with address information etc...

I guess it really depends on what you want to use the drive for, if it's transferring media/documents etc and not running the OS, then it would be just fine for most.

With a NAS you would also have the bonus of being able to share the resource with more PC's easily if you wanted

Alternatively you could use a SATA controller PCI card and attach more devices...although I am not sure when you would reach a critical limit where the system bus would not cope anymore?

---

### Post by bonfire89 on 2009-01-20
yeah, the NAS route would be slower, but, I'm not too worried about that. I mostly feel that I could be wasting money.

The big problem is just fitting the drives in the case.

then even finding a PCI SATA controller that works.


I have one card that works with smaller drivers, and then I bought a new one, but is a piece of.... I got it from tigerdirect.ca (online store that has retail stores aswell) and 1 of the 2 sata connectors functioned extremely slowly. I brought it back to the store and convinced them to exchange it even though I bought it online. The new one functioned the same way. so I don't know if it was a bad batch or what. Paying for shipping to send the card back seems stupid... especially since they may not even do anything.

If I decide to try another controller, I will be sure to buy it at a real store and make sure that there are returns or what not.

---

### Post by mixmaster on 2009-01-20
You could put the drive(s) in a USB enclosure and use one of these:
[http://www.reghardware.co.uk/2009/01/19/review_storage_addonics_nas_adaptor/](http://www.reghardware.co.uk/2009/01/19/review_storage_addonics_nas_adaptor/)

Caveat - I've never tried this device ... I just noticed the review the other day.

---

### Post by kaivalagi on 2009-01-20
When I made the switch from PATA to SATA (< 2 years ago) I bought a cheap NAS enclosure to use with one of my old PATA drives. It supports ethernet (just 100Mbit I think) and usb2 and cost me £30. It works just fine to store pictures and mp3s on for the family to share and upload to. It's been in use for about 2 years and hasn't failed yet.

The page for it in the UK is here: [http://www.cclonline.com/product-info.asp?product_id=12288&category_id=589&manufacturer_id=0&tid=hd-usb2eth](http://www.cclonline.com/product-info.asp?product_id=12288&category_id=589&manufacturer_id=0&tid=hd-usb2eth)

It now costs £22...

Maybe something like this is all you need? Do you have some spare PATA drives anywhere?

P.S. The fan is noisy, so I removed it's connection to the main circuit board....it never overheats.

Just a thought :)

Edit: E-SATA/USB enclosure for £22...[http://www.cclonline.com/product-info.asp?product_id=7927&category_id=589&manufacturer_id=0](http://www.cclonline.com/product-info.asp?product_id=7927&category_id=589&manufacturer_id=0)

---

### Post by bonfire89 on 2009-01-22
yeah, interesting stuff. I'd want to be able have multiple drives in the enclosure.. NAS...

getting 4 drives in would be reasonable.

Could always have a collection of external enclosures. 

I'm sure the speeds would be fine. Most of the time the drives aren't even doing anything.

Interesting.

Well that seems to be about all I will get on this one, so, marking it as solved.

Thanks for the replies.


though, lately I have been finding I am not able to mark threads as solved. I don't understand =/

---

### Post by kaivalagi on 2009-01-22
Thanks, solved etc has been removed temporarily whilst the forums go through some maintenance I think

Good luck

---

