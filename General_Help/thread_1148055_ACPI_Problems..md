---
title: "ACPI Problems."
date: 2009-05-04
forum: General Help
---

### Post by cloverhill on 2009-05-04
[FONT=Courier New]I've installed Ubuntu more than once. It works fine, but I keep receiving a large amount of error and exception messages in my system logs. Using "System Log Viewer" I've received these messages in messages, kern.log, syslog, and I'm not sure where else:

ACPI Error (psargs-0358 ): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND

ACPI Error (psparse-0524): Method parse/execution failed [\_GPE._L1C] (Node ...), AE_NOT_FOUND

ACPI Exception (evgpe-0571): AE_NOT_FOUND, while evaluating GPE method [_L1C]

I've received them over and over again, well over a hundred times. I've had no apparent problems with anything. I've had the exact same thing happen before, when I had Fedora installed. I never had apparent problems, except that when using Fedora, it did seem to be overheating too often. In a cool room, the fan was coming on constantly. Using Ubuntu, the fan is much quieter, though. I've seen some description of what ACPI does, but I've been able to find nothing concerning errors. Also, I'm not exactly sure that in Fedora the error messages were the exact same, but I know they were at least close to being identical, and I received them many, many times also. In Fedora, however, almost every time I ran a program, even a tiny program, the fan would come on and I would sometimes get pretty large amounts of CPU usage with nothing running or open.
[/FONT]

---

### Post by cloverhill on 2009-05-05
Can anyone tell me a site or book or free ebook that has information on something like troubleshooting acpi or similar content? I have fewer messages now, but I am still receiving the same error messages. I've tried many different things to get rid of them. I've tried changing the boot options to acpi=off, no acpi. I've tried reinstalling with no apic and no alpic. I've looked everywhere in help and on the internet I could think of and have found not one troubleshooting guide or any manual or any response anywhere that even points to a solution.
The errors have not changed from the above errors^
Everything seems to be working fine, does anyone think it's not worth worrying about?

---

