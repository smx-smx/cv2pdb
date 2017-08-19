set(CV2PDB_DIR ${CMAKE_CURRENT_SOURCE_DIR})

set(CV2PDB_SOURCES
	src/cv2pdb.cpp
	src/cvutil.cpp
	src/demangle.cpp
	src/dwarf2pdb.cpp
	src/dwarflines.cpp
	src/main.cpp
	src/mspdb.cpp
	src/PEImage.cpp
	src/readDwarf.cpp
	src/symutil.cpp
	#src/dviewhelper/dviewhelper.cpp
)

add_executable(cv2pdb ${CV2PDB_SOURCES})

set(CV2PDB_OUTDIR ${CV2PDB_DIR}/bin)
set_target_properties(cv2pdb
	PROPERTIES
	ARCHIVE_OUTPUT_DIRECTORY ${CV2PDB_OUTDIR}
	LIBRARY_OUTPUT_DIRECTORY ${CV2PDB_OUTDIR}
	RUNTIME_OUTPUT_DIRECTORY ${CV2PDB_OUTDIR}
)

foreach( OUTPUTCONFIG ${CMAKE_CONFIGURATION_TYPES} )
	string( TOUPPER ${OUTPUTCONFIG} OUTPUTCONFIG )
	set_target_properties(cv2pdb
		PROPERTIES
		RUNTIME_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CV2PDB_OUTDIR}
		LIBRARY_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CV2PDB_OUTDIR}
		ARCHIVE_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CV2PDB_OUTDIR}
	)
endforeach( OUTPUTCONFIG CMAKE_CONFIGURATION_TYPES )