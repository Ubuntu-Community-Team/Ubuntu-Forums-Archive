---
title: "Sauerbraten Install Issue"
date: 2007-08-20
forum: Gaming &amp; Leisure
---

### Post by Eion on 2007-08-20
I've searched around and I've yet to find a problem like mine.  I try to "make install" in the correct directory and get this
```
/usr/include/GL/glext.h:6165: error: typedef ‘PFNGLVERTEXBLENDENVFATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6165: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6165: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6175: error: typedef ‘PFNGLELEMENTPOINTERATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6175: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6175: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6176: error: typedef ‘PFNGLDRAWELEMENTARRAYATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6176: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6176: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6177: error: typedef ‘PFNGLDRAWRANGEELEMENTARRAYATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6177: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6177: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6177: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6177: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6185: error: typedef ‘PFNGLDRAWMESHARRAYSSUNPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6185: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6185: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6185: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6185: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6211: error: typedef ‘PFNGLGENOCCLUSIONQUERIESNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6211: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6211: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6211: error: ‘ids’ was not declared in this scope
/usr/include/GL/glext.h:6212: error: typedef ‘PFNGLDELETEOCCLUSIONQUERIESNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6212: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6212: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6213: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6213: error: ‘PFNGLISOCCLUSIONQUERYNVPROC’ was not declared in this scope
/usr/include/GL/glext.h:6214: error: typedef ‘PFNGLBEGINOCCLUSIONQUERYNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6214: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6216: error: typedef ‘PFNGLGETOCCLUSIONQUERYIVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6216: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6216: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6216: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6216: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6217: error: typedef ‘PFNGLGETOCCLUSIONQUERYUIVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6217: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6217: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6217: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6217: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6226: error: typedef ‘PFNGLPOINTPARAMETERINVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6226: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6226: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6227: error: typedef ‘PFNGLPOINTPARAMETERIVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6227: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6227: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6247: error: typedef ‘PFNGLACTIVESTENCILFACEEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6247: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6267: error: typedef ‘PFNGLELEMENTPOINTERAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6267: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6267: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6268: error: typedef ‘PFNGLDRAWELEMENTARRAYAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6268: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6268: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6268: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6269: error: typedef ‘PFNGLDRAWRANGEELEMENTARRAYAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6269: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6269: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6269: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6269: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6269: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6270: error: typedef ‘PFNGLMULTIDRAWELEMENTARRAYAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6270: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6270: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6270: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6270: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6271: error: typedef ‘PFNGLMULTIDRAWRANGEELEMENTARRAYAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6271: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6271: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6271: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6271: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6271: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6271: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6286: error: typedef ‘PFNGLGENFENCESAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6286: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6286: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6286: error: ‘fences’ was not declared in this scope
/usr/include/GL/glext.h:6287: error: typedef ‘PFNGLDELETEFENCESAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6287: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6287: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6288: error: typedef ‘PFNGLSETFENCEAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6288: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6289: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6289: error: ‘PFNGLISFENCEAPPLEPROC’ was not declared in this scope
/usr/include/GL/glext.h:6290: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6290: error: ‘PFNGLTESTFENCEAPPLEPROC’ was not declared in this scope
/usr/include/GL/glext.h:6291: error: typedef ‘PFNGLFINISHFENCEAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6291: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6292: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6292: error: ‘PFNGLTESTOBJECTAPPLEPROC’ was not declared in this scope
/usr/include/GL/glext.h:6293: error: typedef ‘PFNGLFINISHOBJECTAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6293: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6293: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6304: error: typedef ‘PFNGLBINDVERTEXARRAYAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6304: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6305: error: typedef ‘PFNGLDELETEVERTEXARRAYSAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6305: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6305: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6306: error: typedef ‘PFNGLGENVERTEXARRAYSAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6306: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6306: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6306: error: ‘arrays’ was not declared in this scope
/usr/include/GL/glext.h:6307: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6307: error: ‘PFNGLISVERTEXARRAYAPPLEPROC’ was not declared in this scope
/usr/include/GL/glext.h:6317: error: typedef ‘PFNGLVERTEXARRAYRANGEAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6317: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6317: error: ‘GLvoid’ was not declared in this scope
/usr/include/GL/glext.h:6317: error: ‘pointer’ was not declared in this scope
/usr/include/GL/glext.h:6318: error: typedef ‘PFNGLFLUSHVERTEXARRAYRANGEAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6318: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6318: error: ‘GLvoid’ was not declared in this scope
/usr/include/GL/glext.h:6318: error: ‘pointer’ was not declared in this scope
/usr/include/GL/glext.h:6319: error: typedef ‘PFNGLVERTEXARRAYPARAMETERIAPPLEPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6319: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6319: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6335: error: typedef ‘PFNGLDRAWBUFFERSATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6335: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6335: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6368: error: typedef ‘PFNGLPROGRAMNAMEDPARAMETER4FNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6368: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6368: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6368: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6368: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6368: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6368: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6368: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: typedef ‘PFNGLPROGRAMNAMEDPARAMETER4DNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6369: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6369: error: ‘GLdouble’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: ‘GLdouble’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: ‘GLdouble’ was not declared in this scope
/usr/include/GL/glext.h:6369: error: ‘GLdouble’ was not declared in this scope
/usr/include/GL/glext.h:6370: error: typedef ‘PFNGLPROGRAMNAMEDPARAMETER4FVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6370: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6370: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6370: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6370: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6371: error: typedef ‘PFNGLPROGRAMNAMEDPARAMETER4DVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6371: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6371: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6371: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6371: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6372: error: typedef ‘PFNGLGETPROGRAMNAMEDPARAMETERFVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6372: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6372: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6372: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6372: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6372: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6373: error: typedef ‘PFNGLGETPROGRAMNAMEDPARAMETERDVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6373: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6373: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6373: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6373: error: ‘GLdouble’ was not declared in this scope
/usr/include/GL/glext.h:6373: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6446: error: typedef ‘PFNGLMULTITEXCOORD1HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6446: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6446: error: expected primary-expression before ‘s’
/usr/include/GL/glext.h:6447: error: typedef ‘PFNGLMULTITEXCOORD1HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6447: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6447: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6448: error: typedef ‘PFNGLMULTITEXCOORD2HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6448: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6448: error: expected primary-expression before ‘s’
/usr/include/GL/glext.h:6448: error: expected primary-expression before ‘t’
/usr/include/GL/glext.h:6449: error: typedef ‘PFNGLMULTITEXCOORD2HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6449: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6449: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6450: error: typedef ‘PFNGLMULTITEXCOORD3HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6450: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6450: error: expected primary-expression before ‘s’
/usr/include/GL/glext.h:6450: error: expected primary-expression before ‘t’
/usr/include/GL/glext.h:6450: error: expected primary-expression before ‘r’
/usr/include/GL/glext.h:6451: error: typedef ‘PFNGLMULTITEXCOORD3HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6451: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6451: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6452: error: typedef ‘PFNGLMULTITEXCOORD4HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6452: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6452: error: expected primary-expression before ‘s’
/usr/include/GL/glext.h:6452: error: expected primary-expression before ‘t’
/usr/include/GL/glext.h:6452: error: expected primary-expression before ‘r’
/usr/include/GL/glext.h:6452: error: expected primary-expression before ‘q’
/usr/include/GL/glext.h:6453: error: typedef ‘PFNGLMULTITEXCOORD4HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6453: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6453: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6460: error: typedef ‘PFNGLVERTEXATTRIB1HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6460: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6460: error: expected primary-expression before ‘x’
/usr/include/GL/glext.h:6461: error: typedef ‘PFNGLVERTEXATTRIB1HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6461: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6461: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6462: error: typedef ‘PFNGLVERTEXATTRIB2HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6462: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6462: error: expected primary-expression before ‘x’
/usr/include/GL/glext.h:6462: error: expected primary-expression before ‘y’
/usr/include/GL/glext.h:6463: error: typedef ‘PFNGLVERTEXATTRIB2HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6463: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6463: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6464: error: typedef ‘PFNGLVERTEXATTRIB3HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6464: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6464: error: expected primary-expression before ‘x’
/usr/include/GL/glext.h:6464: error: expected primary-expression before ‘y’
/usr/include/GL/glext.h:6464: error: expected primary-expression before ‘z’
/usr/include/GL/glext.h:6465: error: typedef ‘PFNGLVERTEXATTRIB3HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6465: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6465: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6466: error: typedef ‘PFNGLVERTEXATTRIB4HNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6466: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6466: error: expected primary-expression before ‘x’
/usr/include/GL/glext.h:6466: error: expected primary-expression before ‘y’
/usr/include/GL/glext.h:6466: error: expected primary-expression before ‘z’
/usr/include/GL/glext.h:6466: error: expected primary-expression before ‘w’
/usr/include/GL/glext.h:6467: error: typedef ‘PFNGLVERTEXATTRIB4HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6467: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6467: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6468: error: typedef ‘PFNGLVERTEXATTRIBS1HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6468: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6468: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6468: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6469: error: typedef ‘PFNGLVERTEXATTRIBS2HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6469: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6469: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6469: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6470: error: typedef ‘PFNGLVERTEXATTRIBS3HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6470: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6470: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6470: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6471: error: typedef ‘PFNGLVERTEXATTRIBS4HVNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6471: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6471: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6471: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6480: error: typedef ‘PFNGLPIXELDATARANGENVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6480: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6480: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6480: error: ‘GLvoid’ was not declared in this scope
/usr/include/GL/glext.h:6480: error: ‘pointer’ was not declared in this scope
/usr/include/GL/glext.h:6481: error: typedef ‘PFNGLFLUSHPIXELDATARANGENVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6481: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6491: error: typedef ‘PFNGLPRIMITIVERESTARTINDEXNVPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6491: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6508: error: expected initializer before ‘*’ token
/usr/include/GL/glext.h:6509: error: typedef ‘PFNGLUNMAPOBJECTBUFFERATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6509: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6518: error: typedef ‘PFNGLSTENCILOPSEPARATEATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6518: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6518: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6518: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6518: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6519: error: typedef ‘PFNGLSTENCILFUNCSEPARATEATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6519: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6519: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6519: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6519: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: typedef ‘PFNGLVERTEXATTRIBARRAYOBJECTATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6529: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLboolean’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6529: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6530: error: typedef ‘PFNGLGETVERTEXATTRIBARRAYOBJECTFVATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6530: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6530: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6530: error: ‘GLfloat’ was not declared in this scope
/usr/include/GL/glext.h:6530: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6531: error: typedef ‘PFNGLGETVERTEXATTRIBARRAYOBJECTIVATIPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6531: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6531: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6531: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6531: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6543: error: typedef ‘PFNGLDEPTHBOUNDSEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6543: error: ‘GLclampd’ was not declared in this scope
/usr/include/GL/glext.h:6543: error: ‘GLclampd’ was not declared in this scope
/usr/include/GL/glext.h:6555: error: typedef ‘PFNGLBLENDEQUATIONSEPARATEEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6555: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6555: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6607: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6607: error: ‘PFNGLISRENDERBUFFEREXTPROC’ was not declared in this scope
/usr/include/GL/glext.h:6608: error: typedef ‘PFNGLBINDRENDERBUFFEREXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6608: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6608: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6609: error: typedef ‘PFNGLDELETERENDERBUFFERSEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6609: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6609: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6610: error: typedef ‘PFNGLGENRENDERBUFFERSEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6610: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6610: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6610: error: ‘renderbuffers’ was not declared in this scope
/usr/include/GL/glext.h:6611: error: typedef ‘PFNGLRENDERBUFFERSTORAGEEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6611: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6611: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6611: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6611: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6612: error: typedef ‘PFNGLGETRENDERBUFFERPARAMETERIVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6612: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6612: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6612: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6612: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6613: error: typedef ‘GLboolean’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6613: error: ‘PFNGLISFRAMEBUFFEREXTPROC’ was not declared in this scope
/usr/include/GL/glext.h:6614: error: typedef ‘PFNGLBINDFRAMEBUFFEREXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6614: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6614: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6615: error: typedef ‘PFNGLDELETEFRAMEBUFFERSEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6615: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6615: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6616: error: typedef ‘PFNGLGENFRAMEBUFFERSEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6616: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6616: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6616: error: ‘framebuffers’ was not declared in this scope
/usr/include/GL/glext.h:6617: error: typedef ‘GLenum’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6617: error: ‘PFNGLCHECKFRAMEBUFFERSTATUSEXTPROC’ was not declared in this scope
/usr/include/GL/glext.h:6618: error: typedef ‘PFNGLFRAMEBUFFERTEXTURE1DEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6618: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6618: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6618: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6618: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6618: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6619: error: typedef ‘PFNGLFRAMEBUFFERTEXTURE2DEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6619: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6619: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6619: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6619: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6619: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: typedef ‘PFNGLFRAMEBUFFERTEXTURE3DEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6620: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6620: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6621: error: typedef ‘PFNGLFRAMEBUFFERRENDERBUFFEREXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6621: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6621: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6621: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6621: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6622: error: typedef ‘PFNGLGETFRAMEBUFFERATTACHMENTPARAMETERIVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6622: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6622: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6622: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6622: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6622: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6623: error: typedef ‘PFNGLGENERATEMIPMAPEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6623: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6631: error: typedef ‘PFNGLSTRINGMARKERGREMEDYPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6631: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6631: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6643: error: typedef ‘PFNGLSTENCILCLEARTAGEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6643: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6643: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: typedef ‘PFNGLBLITFRAMEBUFFEREXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLint’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLbitfield’ was not declared in this scope
/usr/include/GL/glext.h:6655: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6663: error: typedef ‘PFNGLRENDERBUFFERSTORAGEMULTISAMPLEEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6663: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6663: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6663: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6663: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6663: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6676: error: typedef ‘PFNGLGETQUERYOBJECTI64VEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6676: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6676: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6676: error: expected primary-expression before ‘*’ token
/usr/include/GL/glext.h:6676: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6677: error: typedef ‘PFNGLGETQUERYOBJECTUI64VEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6677: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6677: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6677: error: expected primary-expression before ‘*’ token
/usr/include/GL/glext.h:6677: error: ‘params’ was not declared in this scope
/usr/include/GL/glext.h:6686: error: typedef ‘PFNGLPROGRAMENVPARAMETERS4FVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6686: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6686: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6686: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6686: error: expected primary-expression before ‘const’
/usr/include/GL/glext.h:6687: error: typedef ‘PFNGLPROGRAMLOCALPARAMETERS4FVEXTPROC’ is initialized (use __typeof__ instead)
/usr/include/GL/glext.h:6687: error: ‘GLenum’ was not declared in this scope
/usr/include/GL/glext.h:6687: error: ‘GLuint’ was not declared in this scope
/usr/include/GL/glext.h:6687: error: ‘GLsizei’ was not declared in this scope
/usr/include/GL/glext.h:6687: error: expected primary-expression before ‘const’
make: *** [shared/tools.o] Error 1
mcadams@mcadams-desktop:~/Desktop/sauerbraten/src$ 


```

I have no clue what's going on here.  Sorry if its a n00b mistake.  Im kinda new to Linux.

Thanks in advance!

Eion

---

### Post by GFree678 on 2007-08-21
Compiling something of this level of complexity requires more skill than a n00b should have to experience. :)

Go here instead - [http://sourceforge.net/project/showfiles.php?group_id=102911](http://sourceforge.net/project/showfiles.php?group_id=102911)

Download **sauerbraten_2007_08_19_summer_edition_linux.tar.bz2**

Unpack it and run the **sauerbraten_unix** binary. No compiling required, it's already been done.

EDIT: Last time I tried the game I was using the previous version, the spring edition. If there's a chance they removed the binaries in the new version, you'll have to download the spring edition if you want pre-built binaries. Once again though, since I haven't tried the latest version I can't say if it has binaries or not.

---

### Post by Eion on 2007-08-21
Thanks for the n00b friendly Install advice, i'll check back in a sec to tell you that it worked (I hope :lolflag:)

---

### Post by Eion on 2007-08-21
It says 

```

mcadams@mcadams-desktop:~$ cd /home/mcadams/Desktop/sauerbraten
mcadams@mcadams-desktop:~/Desktop/sauerbraten$ ./sauerbraten_unix
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
mcadams@mcadams-desktop:~/Desktop/sauerbraten$ 

```

Whats the recommended course of action?

---

### Post by j.miller565 on 2007-08-21
that's kind of random. do you have SDL, SDL-image, SDL-mixer, and OpenGL libraries installed?

---

### Post by zero244 on 2007-08-21
Hello I just install that game a few minutes ago. Its a very cool game.
I downloaded it from a deb file which you just double click on.
You need to download the first two files the larger data deb and the smaller executable file.
Install the larger deb file first then the other one.
It will then show up in your games menu.
There are several servers to play online with other people.
This connection where I downloaded it is very fast it should take more than a few minutes to download if you have a decent connection.

[http://www.getdeb.net/](http://www.getdeb.net/)

There are several good games and programs here.
check it out.
Good luck.

Just make sure you download the first two files and install the larger data file first. The smaller file wont install till you install the Data File.

---

### Post by hikaricore on 2007-08-21
> **zero244 said:**
> Hello I just install that game a few minutes ago. Its a very cool game.
I downloaded it from a deb file which you just double click on.
You need to download the first two files the larger data deb and the smaller executable file.
Install the larger deb file first then the other one.
It will then show up in your games menu.
There are several servers to play online with other people.
This connection where I downloaded it is very fast it should take more than a few minutes to download if you have a decent connection.

[http://www.getdeb.net/](http://www.getdeb.net/)

There are several good games and programs here.
check it out.
Good luck.

Just make sure you download the first two files and install the larger data file first. The smaller file wont install till you install the Data File.

I believe this topic pertains to the "Summer" release of Sauerbraten which is not on getdeb.net yet.

---

### Post by zero244 on 2007-08-21
Sorry I didnt know there was more than one release. I will check it out myself.
The version I have is a good game and seems to work very well.

---

