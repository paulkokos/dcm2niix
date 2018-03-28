## About

dcm2niix attempts to convert GE DICOM format images to NIfTI.

## dcm2niix Notes

In addition to reading the


In addition to the public DICOM tags, dcm2niix attempts to decode the proprietary GE Protocol Data Block (0025,101B). This is essentially a [GZip format](http://www.onicos.com/staff/iz/formats/gzip.html) file embedded inside the DICOM header. Here are comments regarding the usage of this data block:

 - The VIEWORDER tag is used to set the polarity of the BIDS tag PhaseEncodingDirection, with VIEWORDER of 1 suggesting bottom up phase encoding.
 - The SLICEORDER tag is used to set the SliceTiming for the BIDS tag PhaseEncodingDirection, with a SLICEORDER of 1 suggesting interleaved acquisition. Note that current versions of dcm2niix do not detect multiband for GE datasets. Therefore, the slice timing reported in the BIDS header will be incorrect for multiband acquisitions.
 - There are reports that newer versions of GE equipement (e.g. DISCOVERY MR750 / 24\MX\MR Software release:DV24.0_R01_1344.a) are now storing an [XML](https://groups.google.com/forum/#!msg/comp.protocols.dicom/mxnCkv8A-i4/W_uc6SxLwHQJ) file within the Protocolo Data Block (compressed). Since the developers of dcm2niix have not had access to any of these files, dcm2niix should generate a warning when it encounters any of these images.

```
POSITION "Supine"
ENTRY "Head First"
CLINICALCOIL "C-GE_32Ch Head"
COIL "32Ch Head"
COILCOMPONENT "32 Ch Head Coil"
PLANE "AXIAL"
SEDESC "Axial rsfMRI (Eyes Open)"
HOS "0"
IMODE "2D"
PSEQ "Gradient Echo"
IOPT "MPh, EPI"
PLUG "9"
IEC_ACCEPT "ON"
FILTCHOICE "None"
BWRT "-1"
TRICKSIMG "1"
TAG_SPACE "7"
TAG_TYPE "None"
USERCV0 "1.00"
USERCV_MASK "1"
USERCV_MASK2 "0"
NUMBVALUE "1"
REOPT "1"
FLIPANG "90"
TE "30.0"
NECHO "1"
TR "3000.0"
NUMSHOTS "1"
BPMMODE "0"
AUTOTRGTYPE "0"
INITSTATE "0"
PSDTRIG "0"
SLICEORDER "1"
VIEWORDER "1"
TRREST "0"
TRACTIVE "0"
SLPERLOC "200"
ACQORDER "0"
DELACQ "Minimum"
DELACQNOAV "2"
SEPSERIES "0"
AUTOTRIGWIN "0"
FOV "22.0"
SLTHICK "3.4"
SPC "0.0"
GRXOPT "0"
SLOC1 "R0.5"
SLOC2 "A27.0"
SLOC3 "I63.3"
ELOC1 "R0.5"
ELOC2 "A27.0"
ELOC3 "S96.5"
FOVCNT1 "R0.5"
FOVCNT2 "A27.0"
NOSLC "48"
SL3PLANE "0"
SL3PLANE1 "0"
SL3PLANE2 "0"
SL3PLANE3 "0"
SPCPERPLANE1 "0.0"
SPCPERPLANE2 "0.0"
SPCPERPLANE3 "0.0"
MATRIXX "64"
MATRIXY "64"
SWAPPF "R/L"
NEX "1.00"
CONTRAST "No"
CONTAM "Yes   "
TBLDELTA "0.00"
PHASEFOV "1.00"
AUTOSHIM "Off"
PHASECORR "Yes"
PAUSEDELMASKACQ "1"
GRIP_SLGROUP1 "0.500000 26.985256 16.641255 0.000000 0.000000 1.000000 0.000000 1.000000 0.000000 1.000000 0.000000 0.000000 48 0.000000 1 0.000000 0"
GRIP_NUMSLGROUPS "1"
GRIP_TRACKER "0"
GRIP_SPECTRO "0"
GRIP_NUMPSCVOL "0"
GRIP_PSCVOL1 "0"
GRIP_PSCVOL2 "0"
GRIP_PSCVOLFOV "0.000000"
GRIP_PSCVOLTHICK "0.000000"
GRIP_IRBAND_A "0"
GRIP_IRBAND_B "0"
AUTOSUBOPTIONS "0"
AUTOSCIC "0"
AUTOVOICE "0"
PRESETDELAY "0.0"
MASKPHASE "0"
MASKPAUSE "0"
GRXLOCSAVE "0"
AUTOCOIL "0"
ONETOUCHREG "0"
TEMPORALPHASES "4"
MEGFREQ "60"
DRIVERAMP "50"
MEGDIR "4"
DRIVERFREQ "60"
RFDRIVEMODE "Quadrature"
INRANGETR "0"
NAVPSCPAUSE "0"
EXCITATIONMODE "Selective"
ANATOMY "SRT%5CNone%5CT-A0100"
```