---
title: "[SOLVED] Dell users of laptops/portables - need YOUR help please"
date: 2008-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Linicks on 2008-11-11
There has been an issue with certain Dell laptops/portables, and the kernel guys have fixed it up - but it appears each Dell laptop/portable sometimes issues a different VENDOR id... and this obviously is unknown to be able to code for.

So if you have a Dell laptop/portable, please post the output of this command:

```
sudo dmidecode | grep -i -a1 -b1 vendor; sudo dmidecode | grep -i -a1 -b1 "Product Name"
```

You should get something like this:

> 
1814-BIOS Information
1831:   Vendor: Dell Inc.
1850-   Version: A17
2774-   Manufacturer: Dell Inc.
2799:   Product Name: MM061
2847-   Version: Not Specified
--
3064-   Manufacturer: Dell Inc.
3089:   Product Name: 0KD882
3111-   Version:



Thats all tht is needed - no more fluff to the posts please so it is easy to parse.

This will help a lot to capture all the variants Dell BIOS uses.

Thanks,

Nick

---

### Post by ddarsow on 2008-11-11
2675-BIOS Information
2692:	Vendor: Dell Inc.
2711-	Version: A02
3546-	Manufacturer: Dell Inc.
3571:	Product Name: Latitude D620                   
3619-	Version: Not Specified
--
3836-	Manufacturer: Dell Inc.
3861:	Product Name: 0JK187
3883-	Version:

---

### Post by JinStevens on 2008-11-11
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A13
3093-	Manufacturer: Dell Inc.
3118:	Product Name: Inspiron 1525                   
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name: 0U990C
3430-	Version:

---

### Post by solitaire on 2008-11-11
841-BIOS Information
858:    Vendor: Dell Computer Corporation
893-    Version: A11
1782-    Manufacturer: Dell Computer Corporation
1823:    Product Name: Inspiron 8200                   
1871-    Version: Not Specified
--
2050-    Manufacturer: Dell Computer Corporation
2091:    Product Name: Inspiron 8200            
2132-    Version: Not Specified

---

### Post by NE Key on 2008-11-11
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A11
3093-	Manufacturer: Dell Inc.
3118:	Product Name: Inspiron 1525                   
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name: 0U990C
3430-	Version:

---

### Post by superm1 on 2008-11-11
> **Linicks said:**
> There has been an issue with certain Dell laptops/portables, and the kernel guys have fixed it up - but it appears each Dell laptop/portable sometimes issues a different VENDOR id... and this obviously is unknown to be able to code for.

So if you have a Dell laptop/portable, please post the output of this command:

```
sudo dmidecode | grep -i -a1 -b1 vendor; sudo dmidecode | grep -i -a1 -b1 "Product Name"
```You should get something like this:




Thats all tht is needed - no more fluff to the posts please so it is easy to parse.

This will help a lot to capture all the variants Dell BIOS uses.

Thanks,

Nick
Sorry to add "fluff", but what kernel issue are you referring to?

---

### Post by bd_thompson on 2008-11-11
[QUOTE=Linicks;6153717]There has been an issue with certain Dell laptops/portables, and the kernel guys have fixed it up - but it appears each Dell laptop/portable sometimes issues a different VENDOR id... and this obviously is unknown to be able to code for.

617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: A00
1140-	Manufacturer: Dell Inc.
1165:	Product Name: Inspiron 910
1193-	Version: A00
--
1412-	Manufacturer: Dell Inc.
1437:	Product Name: CN0J14
1459-	Version: A00

---

### Post by Linicks on 2008-11-11
> **superm1 said:**
> Sorry to add "fluff", but what kernel issue are you referring to?

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/285323](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/285323)

The kernel patch addresses the issue, but it was found out that some Dell laptops/portables declare the vendor ID different.

Unless we can get a list of models/vendor ID, it would be impossible to do this.

I have replied to the kernel people, and hopefully if we can get a list together, it will help out enormously.

[http://marc.info/?l=linux-kernel&m=122638966722351&w=2](http://marc.info/?l=linux-kernel&m=122638966722351&w=2)

Nick

---

### Post by KayakJim on 2008-11-11
1852-BIOS Information
1869:	Vendor: Dell Inc.
1888-	Version: A09
2812-	Manufacturer: Dell Inc.
2837:	Product Name: MP061                           
2885-	Version: Not Specified
--
3102-	Manufacturer: Dell Inc.
3127:	Product Name: 0YD479
3149-	Version:

---

### Post by firstcupoffreshpressed on 2008-11-12
372-BIOS Information
389:	Vendor: Dell Computer Corporation
424-	Version: A34
1278-	Manufacturer: Dell Computer Corporation
1319:	Product Name: Inspiron 5150                   
1367-	Version: Not Specified
--
1546-	Manufacturer: Dell Computer Corporation
1587:	Product Name: 0W0940
1609-	Version:

---

### Post by Mountaineer on 2008-11-12
2094-BIOS Information
2111:	Vendor: Dell Inc.
2130-	Version: A09
3055-	Manufacturer: Dell Inc.
3080:	Product Name: Inspiron 1720                   
3128-	Version: Not Specified
--
3345-	Manufacturer: Dell Inc.
3370:	Product Name:       
3392-	Version:

---

### Post by Linicks on 2008-11-12
OK Guys, thanks very much.

All I need now is only any output that DOESN'T state the Vendor as 'Dell Inc.' or 'Dell Computer Corporation' (exactly matching).

Thnaks,

Nick

---

### Post by sinanimam on 2008-11-12
2094-BIOS Information
2111:	Vendor: Dell Inc.
2130-	Version: A10
3055-	Manufacturer: Dell Inc.
3080:	Product Name: XPS M1330                       
3128-	Version: Not Specified
--
3345-	Manufacturer: Dell Inc.
3370:	Product Name: 0N6705
3392-	Version:

---

### Post by budde on 2008-11-13
2206-BIOS Information
2223:	Vendor: Dell Inc.
2242-	Version: A02
3077-	Manufacturer: Dell Inc.
3102:	Product Name: MXC062                          
3150-	Version: Not Specified
--
3367-	Manufacturer: Dell Inc.
3392:	Product Name: 0FP985
3414-	Version:

---

### Post by iaskedalice09 on 2008-11-13
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A13
3093-	Manufacturer: Dell Inc.
3118:	Product Name: Inspiron 1525                   
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name: 0U990C
3430-	Version:

---

### Post by Diggs808 on 2008-11-13
2899-BIOS Information
2916:    Vendor: Dell Inc.
2935-    Version: A12
3860-    Manufacturer: Dell Inc.
3885:    Product Name: Latitude D830                   
3933-    Version: Not Specified
--
4150-    Manufacturer: Dell Inc.
4175:    Product Name: 0UY141
4197-    Version:

---

### Post by MartijnV on 2008-11-13
841-BIOS Information
858:	Vendor: Dell Computer Corporation
893-	Version: A16
1782-	Manufacturer: Dell Computer Corporation
1823:	Product Name: Latitude C610                   
1871-	Version: Not Specified
--
2050-	Manufacturer: Dell Computer Corporation
2091:	Product Name: Latitude C610            
2132-	Version: Not Specified

---

### Post by starcannon on 2008-11-14
617-BIOS Information
634:    Vendor: Dell Inc.
653-    Version: A00
1140-    Manufacturer: Dell Inc.
1165:    Product Name: Inspiron 910
1193-    Version: A00
--
1412-    Manufacturer: Dell Inc.
1437:    Product Name: CN0J14
1459-    Version: A00

---

### Post by kezdetj on 2008-11-14
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A09
3093-	Manufacturer: Dell Inc.
3118:	Product Name: XPS M1530                       
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name: 0D501F
3430-	Version:

---

### Post by Linicks on 2008-11-15
OK, that's enough folks!

There is enough info now.

Thanks,

Nick

---

### Post by loneowais on 2008-11-17
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A13
3093-	Manufacturer: Dell Inc.
3118:	Product Name: Inspiron 1525                   
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name:       
3430-	Version:

---

### Post by KayakJim on 2008-12-17
446-BIOS Information
463:    Vendor: Dell Inc.
482-    Version: A09
1317-   Manufacturer: Dell Inc.
1342:   Product Name: Inspiron 6000
1390-   Version: Not Specified
--
1569-   Manufacturer: Dell Inc.
1594:   Product Name: 0X9238
1616-   Version:

---

### Post by SGB48140 on 2008-12-21
2973-BIOS Information
2990:	Vendor: Dell Inc.
3009-	Version: A10
3934-	Manufacturer: Dell Inc.
3959:	Product Name: Latitude E6500                  
4007-	Version: Not Specified
--
4224-	Manufacturer: Dell Inc.
4249:	Product Name: 0PP476
4271-	Version:

---

### Post by IEKnight on 2008-12-21
617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: 2.6.1    
--
9258-	Operation: Unknown
9278:	Vendor Syndrome: Unknown
9304-	Memory Array Address: Unknown
1640-	Manufacturer: Dell Inc.
1665:	Product Name: Inspiron 1501 
1695-	Version: Not Specified                   
--
1943-	Manufacturer: Dell Inc.
1968:	Product Name: 0UW953
1990-	Version:

---

### Post by firefox66 on 2008-12-21
2899-BIOS Information
2916:   Vendor: Dell Inc.
2935-   Version: A13
3860-   Manufacturer: Dell Inc.
3885:   Product Name: Latitude D830
3933-   Version: Not Specified
--
4150-   Manufacturer: Dell Inc.
4175:   Product Name: 0UY141
4197-   Version:

---

### Post by Eduardo Mercovich on 2008-12-22
> **Linicks said:**
> There has been an issue with certain Dell laptops/portables, and the kernel guys have fixed it up [...]
So if you have a Dell laptop/portable, please post the output of this command:
```
sudo dmidecode | grep -i -a1 -b1 vendor; sudo dmidecode | grep -i -a1 -b1 "Product Name"
```


2132-BIOS Information
2149:   Vendor: Dell Inc.
2168-   Version: A11
3093-   Manufacturer: Dell Inc.
3118:   Product Name: Inspiron 1525                   
3166-   Version: Not Specified
--
3383-   Manufacturer: Dell Inc.
3408:   Product Name: 0U990C
3430-   Version:   

Regards...

--
EM

---

### Post by p388l3s on 2008-12-22
617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: A02
sudo: unable to resolve host dino-m9-hh
1140-	Manufacturer: Dell Inc.
1165:	Product Name: Inspiron 910
1193-	Version: A02
--
1412-	Manufacturer: Dell Inc.
1437:	Product Name: CN0J14
1459-	Version: A02

---

### Post by Accidus on 2008-12-29
Here's mine, I thought it was weird that the fixes didn't apply to my machine. Does this mean other Dell-related bugs will be solved when this fix is merged?

```

1664-BIOS Information
1681:   Vendor: Dell Inc.
1700-   Version: A01
2626-   Manufacturer: Dell Inc.
2651:   Product Name: Inspiron 1545
2699-   Version: Not Specified
--
2916-   Manufacturer: Dell Inc.
2941:   Product Name: 0G848F
2963-   Version:

```

---

### Post by ocarlson on 2008-12-29
823-BIOS Information
840:	Vendor: Dell Computer Corporation
875-	Version: A20
1679-	Manufacturer: Dell Computer Corporation
1720:	Product Name: Latitude C600                   
1768-	Version: Not Specified
--
1947-	Manufacturer: Dell Computer Corporation
1988:	Product Name: Latitude C600            
2029-	Version: Not Specified

---

### Post by llamakc on 2008-12-29
2132-BIOS Information
2149:    Vendor: Dell Inc.
2168-    Version: A16
3093-    Manufacturer: Dell Inc.
3118:    Product Name: Inspiron 1525                   
3166-    Version: Not Specified
--
3383-    Manufacturer: Dell Inc.
3408:    Product Name: 0U990C
3430-    Version:

---

### Post by marsopia on 2008-12-30
2094-BIOS Information
2111:	Vendor: Dell Inc.
2130-	Version: A08
3055-	Manufacturer: Dell Inc.
3080:	Product Name: Inspiron 1420                   
3128-	Version: Not Specified
--
3345-	Manufacturer: Dell Inc.
3370:	Product Name: 0DT492
3392-	Version:

---

### Post by eyime on 2009-01-01
2094-BIOS Information
2111:	Vendor: Dell Inc.
2130-	Version: A14
3055-	Manufacturer: Dell Inc.
3080:	Product Name: XPS M1330                       
3128-	Version: Not Specified
--
3345-	Manufacturer: Dell Inc.
3370:	Product Name: 0N6705
3392-	Version:

---

### Post by richardrblc on 2009-01-02
617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: 2.6.3    
--
9222-	Operation: Unknown
9242:	Vendor Syndrome: Unknown
9268-	Memory Array Address: Unknown
1640-	Manufacturer: Dell Inc.
1665:	Product Name: Inspiron 1501 
1695-	Version: Not Specified                   
--
1943-	Manufacturer: Dell Inc.
1968:	Product Name: 0UW744
1990-	Version:

---

### Post by anjilslaire on 2009-01-02
```

617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: A03
1140-	Manufacturer: Dell Inc.
1165:	Product Name: Inspiron 910
1193-	Version: A03
--
1412-	Manufacturer: Dell Inc.
1437:	Product Name: CN0J14
1459-	Version: A03

```

---

### Post by CancelloCornorosso on 2009-01-03
2094-BIOS Information
2111:	Vendor: Dell Inc.
2130-	Version: A12
3055-	Manufacturer: Dell Inc.
3080:	Product Name: XPS M1330                       
3128-	Version: Not Specified
--
3345-	Manufacturer: Dell Inc.
3370:	Product Name: 0N6705
3392-	Version:

---

### Post by AmyRose on 2009-01-03
2132-BIOS Information
2149:	Vendor: Dell Inc.
2168-	Version: A16
3093-	Manufacturer: Dell Inc.
3118:	Product Name: Inspiron 1525                   
3166-	Version: Not Specified
--
3383-	Manufacturer: Dell Inc.
3408:	Product Name: 0U990C
3430-	Version:

---

### Post by Kareeser on 2009-01-03
You say you're looking for people whose Vendor IDs don't say "Dell"?

Looks like you're looking for me.

261-BIOS Information
278:	Vendor: Phoenix Technologies LTD
312-	Version: A04
809-	Manufacturer: Dell Inc.
834:	Product Name: Inspiron 700m      
869-	Version: -1             
--
1050-	Manufacturer: DELL SYSTEM
1077:	Product Name: 0D9593
1099-	Version:

---

### Post by spikoley on 2009-01-05
523-BIOS Information
540:	Vendor: Dell Computer Corporation
575-	Version: A13
1429-	Manufacturer: Dell Computer Corporation
1470:	Product Name: Latitude D800                   
1518-	Version: Not Specified
--
1697-	Manufacturer: Dell Computer Corporation
1738:	Product Name:       
1760-	Version:

---

### Post by Linicks on 2009-01-05
NO MORE PLEASE - THIS THREAD WAS MARKED *SOLVED* AGES AGO.

==========================================================

Thanks,

Nick

---

### Post by Byr0n_X on 2009-01-05
617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: 2.6.3    
--
9255-	Operation: Unknown
9275:	Vendor Syndrome: Unknown
9301-	Memory Array Address: Unknown
1640-	Manufacturer: Dell Inc.
1665:	Product Name: Vostro   1000 
1695-	Version: Not Specified                   
--
1943-	Manufacturer: Dell Inc.
1968:	Product Name: 0WY383
1990-	Version:

---

### Post by Linicks on 2009-01-05
> **Linicks said:**
> NO MORE PLEASE - THIS THREAD WAS MARKED *SOLVED* AGES AGO.

==========================================================

Thanks,

Nick

FFS

Y'all STOP PLEASE

---

### Post by superm1 on 2009-01-05
> **Linicks said:**
> FFS

Y'all STOP PLEASE
Modify the first post to indicate this thread is no longer necessary so new users dont keep replying after they see the first post...

---

### Post by richardrblc on 2009-01-21
617-BIOS Information
634:	Vendor: Dell Inc.
653-	Version: 2.6.3    
--
9222-	Operation: Unknown
9242:	Vendor Syndrome: Unknown
9268-	Memory Array Address: Unknown
1640-	Manufacturer: Dell Inc.
1665:	Product Name: Inspiron 1501 
1695-	Version: Not Specified                   
--
1943-	Manufacturer: Dell Inc.
1968:	Product Name: 0UW744
1990-	Version:

---

### Post by Cannotcompute on 2009-01-21
Oops... heh heh....

---

### Post by Fredvs79 on 2009-03-23
523-BIOS Information
540:	Vendor: Dell Computer Corporation
575-	Version: A17
1429-	Manufacturer: Dell Computer Corporation
1470:	Product Name: Inspiron 600m                   
1518-	Version: Not Specified
--
1697-	Manufacturer: Dell Computer Corporation
1738:	Product Name:       
1760-	Version:

---

### Post by abn91c on 2009-03-23
.

---

### Post by geoffm on 2009-03-23
2094-BIOS Information
2111:   Vendor: Dell Inc.
2130-   Version: A15
3055-   Manufacturer: Dell Inc.
3080:   Product Name: XPS M1330
3128-   Version: Not Specified
--
3345-   Manufacturer: Dell Inc.
3370:   Product Name: 0N6705
3392-   Version:

---

