// Declarativa: Es más cómoda... más guiada... menos flexible
pipeline {
    // Integración continua
    agent any;
    // Parametros
    parameters {
        booleanParam description: 'Quiere hacer pruebas de HA?', name: 'PROBAR_HA'
        choice choices: ['chrome', 'firefox'], description: 'Qué navegador usar para las pruebas de UI básicas', name: 'NAVEGADOR_PRUEBAS_BASICAS'
    }

    stages {
        stage('1-Compilación') {
            steps {
                echo 'Voy a compilar:'
                echo 'Estoy en ello.....'
                echo 'Listo'
            }
            post {
                success {
                    echo 'Se ejecuta solo si los steps han ido bien'
                }
                failure {
                    echo 'Se ejecuta solo si los steps han ido mal'
                }
                always {
                    echo 'Se ejecuta en cualquier caso'
                }
            }
        }    
