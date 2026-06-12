---
title: "shutdown help!"
date: 2005-09-16
forum: Desktop Environments
---

### Post by blakken on 2005-09-16
when pressing over my power button over my laptop i should normally shutdown as it exectute the script powerbtn.sh unfortunately it doesn't ,here is what my acpi.log read during the event:

09/16/2005 02:03:25 PM	completed event	button/power PWRF 00000080 00000001
09/16/2005 02:03:25 PM	executing action	/etc/acpi/powerbtn.sh
09/16/2005 02:03:25 PM	none	action exited with status 1

09/16/2005 02:03:25 PM	none	BEGIN HANDLER MESSAGES

09/16/2005 02:03:25 PM	none	END HANDLER MESSAGES

09/16/2005 02:03:25 PM	received event	button/power PWRF 00000080 00000001
09/16/2005 02:03:25 PM	none	ERROR: Couldn't attach to DCOP server!

09/16/2005 02:03:25 PM	none	DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

09/16/2005 02:03:25 PM	none	DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

09/16/2005 02:03:25 PM	none	object not accessible

 
any idea about this dcop server ?
 ](*,)

---

