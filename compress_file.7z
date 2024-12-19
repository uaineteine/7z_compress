param(
    [string]$inputFile = "C:\path\to\your\dataset.sas7bdat",
    [string]$outputFile = "C:\path\to\your\dataset.7z",
    [string]$logFile = "C:\path\to\your\compression.log"
)

# Set the variables for compression level and 7-Zip path
$compressionLevel = 9  # Default compression level
$sevenZipPath = "C:\Program Files\7-Zip\7z.exe"  # Default 7-Zip path

# Check if input file exists
if (-Not (Test-Path -Path $inputFile)) {
    Add-Content -Path $logFile -Value "$((Get-Date).ToString('yyyy-MM-dd HH:mm:ss')) - ERROR: Input file $inputFile does not exist."
    exit
}

# Compress the SAS dataset using 7-Zip with the specified compression level
try {
    $result = & $sevenZipPath a -mx=$compressionLevel $outputFile $inputFile
    if ($?) {
        Add-Content -Path $logFile -Value "$((Get-Date).ToString('yyyy-MM-dd HH:mm:ss')) - SUCCESS: Compressed $inputFile to $outputFile with compression level $compressionLevel."
    } else {
        Add-Content -Path $logFile -Value "$((Get-Date).ToString('yyyy-MM-dd HH:mm:ss')) - ERROR: Failed to compress $inputFile to $outputFile. Output: $result"
    }
} catch {
    Add-Content -Path $logFile -Value "$((Get-Date).ToString('yyyy-MM-dd HH:mm:ss')) - ERROR: Failed to compress $inputFile to $outputFile. Exception: $_"
}
