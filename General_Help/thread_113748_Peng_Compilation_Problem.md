---
title: "Peng Compilation Problem"
date: 2006-01-07
forum: General Help
---

### Post by fusionex on 2006-01-07
Hi All,

I would post this at the peng site, but no one seems to use the forums there.  If you guys know a better place I can post this question please let me know.

I try to compile and install peng as an aol dialer using the following command: ./recompile

However, I keep getting this error which is written to a make.log file:

In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from cclienttoaol30.h:24,
                 from kernel30.h:50,
                 from caolcmd30.h:22,
                 from thrmake[2]: Leaving directory `/home/fusionex/peng/peng'
make[1]: Leaving directory `/home/fusionex/peng'
.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:226: error: ISO C++ forbids declaration of ‘CAolCmd30’ with no type
kernel30.h:226: error: expected ‘;’ before ‘*’ token
make[2]: *** [threadELV3.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2

I checked the peng header files for CAolCmd30 and kernel30.h.  CAolCmd30 seems to have no syntax errors, so I don't know why my compiler doesn't realize that CAolCm30 is a class.  I don't know if this a problem with my compiler or the peng source.  I installed g++ from the synaptic package manager.  So, I'm out of ideas.  Thanks to anyone who can help.

---

### Post by Peter76 on 2006-01-07
It says in the last line of the header : "To disable this warning use -Wno-deprecated."
Try something like ./recompile --help, to see how you can pass this to gcc... Or reaad through the documentation and see if something's there about this.

Good luck

---

### Post by fusionex on 2006-01-07
I was able to get rid of the warning by replacing deprecated header files like <iostream.h> with <iostream> and <stdlib.h> with <cstdlib>.  However, I am still getting the following errors in my make.log file that were there in the original make.log I posted above.

Anyways, here it is:

kernel30.h:226: error: ISO C++ forbids declaration of ‘CAolCmd30’ with no type
kernel30.h:226: error: expected ‘;’ before ‘*’ token
make[2]: *** [threadELV3.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
/peng/peng'
make[1]: Leaving directory `/home/fusionex/peng'

I added an attachment to the kernel30.h I modified to this post.  I'll also post as text below so that someone can look at the file without having to open the compressed archive I attached.  The line that says 
	CAolCmd30 * m_cCmd;

is the line that is producing the error.  Thanks to anyone who can help.

/***************************************************************************

                          kernel30.h  -  description

                             -------------------

    begin                : Fri Jun 1 2001

    copyright            : (C) 2001 by stephane (birdy57)

    email                : [email]birdy57@multimania.com[/email]

 ***************************************************************************/

 

/***************************************************************************

 *                                                                         *

 *   This program is free software; you can redistribute it and/or modify  *

 *   it under the terms of the GNU General Public License as published by  *

 *   the Free Software Foundation; either version 2 of the License, or     *

 *   (at your option) any later version.                                   *

 *                                                                         *

 ***************************************************************************/ 

    

#ifndef KERNEL30_H

#define KERNEL30_H

    

#ifdef WIN32

#include <winsock>

#else				/* 
 */
#include <unistd.h>

#include <cstdlib>

#include <cstdio>

#include <termios.h>

#include <sys/fcntl.h>

#include <sys/ioctl.h>

#include <sys/types.h>

#include <sys/socket.h>

#include <sys/un.h>

#include <sys/time.h>

#include <netinet/in.h>

#include <netdb.h>

#include <arpa/inet.h>

#define SOCKET int

#define closesocket close

#endif				/* 
 */
    

#include "nulldriver.h"

#include "ckernel.h"

#include "caolheader30.h"

#include "cvjcompress.h"

#include "caoltoclient30.h"

#include "caolcmd30.h"

#include "cclienttoaol30.h"

    


#define MRUIn	1550

#define MRUOut	1550

    

/**noyau de simulation 3.0

  *@author stephane (birdy57)

  */ 


class Kernel30:public CKernel 
 {
  
public:
Kernel30();
    
~Kernel30();
    
friend class CAolToClient30;
    
friend class CClientToAol30;
    
friend class CAolCmd30;
    

  /** ecrit une sequence Raw en y ajoutant le header AOL */ 

    void WriteRawIn(char *buffer, int nLon);
    

  /** recherche l'adresse IP */ 

	bool FindIp(char *sBuffer, int nLon);
    

  /** Demmare le noyau */ 

    void Start();
    

  /** Connection */ 

	bool Connect(char *Login, char *Pass);
    

  /** donne l'adresse IP */ 

    void GetIp(char *sBuffer);
    

  /** donne le nom de domaine */ 

    void GetDomainName(char *sBuffer);
    

  /** Donne le Dns */ 

    void GetDns(char *sBuffer);
    

  /** arrete le noyau */ 

    void Stop();
  

protected:

class m_CData {
      
public:
const char *dat1;
	
const char *dat2;
	
const char *dat3;
	
const char *dat4;
	
const char *dat5;
	
const char *dat6;
	
const char *dat7;
	
const char *dat8;
	
const char *dat9;
	
const char *dat10;
	
const char *dat11;
	
const char *dat12;
	
const char *dat13;
	
const char *dat14;
	
const char *dat15;
	
const char *dat16;
	
const char *dat17;
	
const char *dat18;
	
const char *dat19;
	
const char *dat20;
    
};
    

class m_CIp {
      
public:
unsigned char Ip1;
	
unsigned char Ip2;
	
unsigned char Ip3;
	
unsigned char Ip4;
	
unsigned char Dns1;
	
unsigned char Dns2;
	
unsigned char Dns3;
	
unsigned char Dns4;
	
char *DomainName;
	
void GetIpStr(char *buffer) {
	    sprintf(buffer, "%d.%d.%d.%d", Ip1, Ip2, Ip3, Ip4);
	};
	
void GetDnsStr(char *buffer) {
	    sprintf(buffer, "%d.%d.%d.%d", Dns1, Dns2, Dns3, Dns4);
	};
    
};
    


  /** donnee */ 

	m_CData * CData;
    

  /** Header aol version 3.0 et cable */ 

	CAolHeader30 * AolHeaderIn;
  

protected:			// Protected methods

  /** Lecture d'un trame AOL , la longueur est retoune */ 

    int ReadAolTrame(char *buffer, int MaxBuffer);
    

  /** recharge la trame nAck,nSeq */ 

    int ReadAolTrameSeqAck(char *buffer, int nBufferSize, int nSeq,
			   int nAck);
    

  /** negociation de la connection */ 

	bool Negociate(char *Login, char *PassWord);
    

  /** Classe Ip */ 

	m_CIp * m_Ip;
    

  /** compresseur */ 

	CVjcompress * VjcompressOut;
    

	// Variables commune au 3 classe du noyau

	
bool bStopTunneling;
    
bool bNeedAck;
    
bool bIDLE;
    
unsigned short m_nNeedAck;
    
unsigned short m_nNeedSeq;
    
bool m_bAckTrame;
    
unsigned short m_nLastAolAck;
    
unsigned short m_nLastAolSeq;
    
unsigned short m_nLastAolInet;
    
unsigned short m_nFirstAolSeq;
    

  /** Classe Cmd */ 

	CAolCmd30 * m_cCmd;
    

  /** classe client->Aol */ 

	CClientToAol30 * m_cClientToAol;
    

  /** classe Aol->client */ 

	CAolToClient30 * m_cAolToClient;
    

  /** ecriture */ 

	bool m_bWriting;

};



#endif				/* 
 */

---

