---
title: "Compiling Ultimate Stunts problem"
date: 2016-07-28
forum: Gaming &amp; Leisure
---

### Post by henriquec on 2016-07-28
Hello comrades.

I'm having some trouble to compile the source code of the game Ultimate Stunts
If someone could help i'd be very grateful.

Here is the error:

```
metaserver.cpp: In member function ‘CString CMetaServer::httpReadBodyNormal()’:
metaserver.cpp:265:47: error: ‘read’ was not declared in this scope
   readLen = read(m_SockFD, writePtr, remainLen);
                                               ^
metaserver.cpp: In member function ‘int CMetaServer::readChar()’:
metaserver.cpp:448:28: error: ‘read’ was not declared in this scope
  n = read(m_SockFD, &ret, 1);
                            ^
metaserver.cpp: In member function ‘CString CMetaServer::readStr(unsigned int)’:
metaserver.cpp:470:37: error: ‘read’ was not declared in this scope
  n = read(m_SockFD, buffer, maxlen-1);
                                     ^
metaserver.cpp: In member function ‘bool CMetaServer::writeStr(const CString&)’:
metaserver.cpp:491:53: error: ‘write’ was not declared in this scope
  int n = write(m_SockFD, data.c_str(), data.length());
                                                     ^
metaserver.cpp: In member function ‘void CMetaServer::tcpDisconnect()’:
metaserver.cpp:544:16: error: ‘close’ was not declared in this scope
  close(m_SockFD);
                ^
Makefile:368: recipe for target 'metaserver.o' failed
make[1]: *** [metaserver.o] Error 1
make[1]: Leaving directory '/home/henrique/Teste/ultimatestunts-srcdata-0771/simulation'
Makefile:332: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1
```

---

