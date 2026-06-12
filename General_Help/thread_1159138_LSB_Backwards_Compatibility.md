---
title: "LSB Backwards Compatibility"
date: 2009-05-14
forum: General Help
---

### Post by mbr5002 on 2009-05-14
Hello,
 
Does anyone know if Linux Standard Base (LSB) is always backwards compatible?
 
For example, I am having trouble getting some software to work that says it must be compatible with LSB version 1.3, but I have a newer version of LSB. Could this be the problem?
 
Thank you!
 
Sincerely,
Matt

---

### Post by mbr5002 on 2009-05-19
If anyone is interested, I found the answer to my question.  (although it didn't solve me problem)
 
[COLOR=#666666][FONT=Arial][SIZE=1]The LSB provides backward compatibility at both the source and binary level beginning with LSB 3.0. In other words, applications that target version X.Y of the LSB (where X.Y >= 3.0) will run on distributions certified to or compliant with LSB version X.Y [/SIZE][/FONT]*[FONT=Arial]and newer[/FONT]*[FONT=Arial][SIZE=1]. For example, applications that target LSB 3.0 will run not only on LSB 3.0 certified/compliant distributions but also LSB 3.1, LSB 3.2, LSB 4.0 etc. certified/compliant distributions.[/SIZE][/FONT][/COLOR]
[FONT=Arial][SIZE=1][COLOR=#666666]To achieve backward compatibility, each subsequent version is purely additive--in other words, interfaces are only added, not removed (our [/COLOR][/SIZE][[COLOR=#003f69][SIZE=1]interface deprecation policy[/SIZE][/COLOR]]("http://ldn.linuxfoundation.org/en/Deprecation_Policy")[SIZE=1][COLOR=#666666] does provide us with a mechanism for removing interfaces, but only after the interfaces have been marked "deprecated" for at least three major versions, or roughly six years).[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=1][COLOR=#666666]This policy allows application vendors to certify to the version of the LSB that provides the interfaces they need and not require them to recertify to newer versions unless the newer versions provide functionality the applications require.[/COLOR][/SIZE][/FONT]
[COLOR=#666666][FONT=Arial][SIZE=1]Please note that the application compatibility policy has changed with LSB 3.0: previously, in LSB 1.x and 2.x, binary compatibility was only provided [/SIZE][/FONT]*[FONT=Arial]within a major version[/FONT]*[FONT=Arial][SIZE=1]--now application compatibility is provided between major versions.[/SIZE][/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Source:  [http://ldn.linuxfoundation.org/lsb/lsb-introduction](http://ldn.linuxfoundation.org/lsb/lsb-introduction)[/SIZE][/FONT]

---

