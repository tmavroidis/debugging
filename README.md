# debugging
Neat trick I just found that you can do with the debugger, you can set it to wide screen mode 27 * 132 (STRDBDWIDE).


Then change it back (ENDDBGWIDE). 


Or you can just run the addenvvar from the command line.


Useful when the source lines are longer than 80 bytes long, saves you from scrolling over.


Compile as CLLE to use.

             /*  Set debugger to 27 * 132 mode                               */
             /* PGM STRDBGWIDE  */            
             /* NTM Consulting Incorporated, Markham, Ontario                */            
             /* 416-258-3577 tmavroidis@ntm.net                              */
             /* Software is licenced under the GNU General Public License V3 */
             /* https://www.gnu.org/licenses/gpl-3.0.htm                     */

             pgm
             
             AddEnvVar  EnvVar('ILE_DEBUGGER_1') +
                          Value('ALLOW_WIDE_SCREEN') Level(*Job) Replace(*Yes)
                          

             endpgm                  
             
             /*  Set debugger to 24 * 80 mode  */
             /* PGM ENDDBGWIDE  *.
             /* NTM Consulting Incorporated, Markham, Ontario                */
             /* 416-258-3577 tmavroidis@ntm.net                              */
             /* Software is licenced under the GNU General Public License V3 */
             /* https://www.gnu.org/licenses/gpl-3.0.htm                     */

             pgm

             RmvEnvVar  EnvVar('ILE_DEBUGGER_1') Level(*Job)

             MONMSG     MSGID(CPFA981)

             endpgm        

Tom
