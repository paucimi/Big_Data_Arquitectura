# Big_Data_Arquitectura

# Arquitectura Big Data: Integración de ElasticSearch y Hadoop

## Español

Este proyecto tiene como objetivo configurar la integración entre un clúster de **Hadoop** y **ElasticSearch**, permitiendo el uso conjunto de estas tecnologías para el procesamiento y análisis de grandes volúmenes de datos.

### Índice

- [Parte 1: Configuración de ES-Hadoop](#parte-1-configuración-de-es-hadoop)
- [Parte 2: Configuración del Servidor ElasticSearch](#parte-2-configuración-del-servidor-elasticsearch)
- [Parte 3: Configuración de la Conexión en el Clúster Hadoop](#parte-3-configuración-de-la-conexión-en-el-clúster-hadoop)
- [Parte 4: Conectar y Consultar Datos](#parte-4-conectar-y-consultar-datos)
- [Parte 5: Uso de Kibana (Opcional)](#parte-5-uso-de-kibana-opcional)

---

### Parte 1: Configuración de ES-Hadoop

1. **Crear un clúster Hadoop**:
   - Utilizar Google Cloud Dataproc para crear un clúster Hadoop estándar o independiente.

2. **Descargar las librerías necesarias**:
   - Obtener los archivos JAR de `elasticsearch-hadoop` y `commons-httpclient`.

3. **Crear un bucket en Google Cloud Storage**:
   - Almacenar los archivos JAR descargados en un bucket para facilitar su acceso desde el clúster.

4. **Subir los JARs al clúster Hadoop**:
   - Copiar los archivos JAR desde el bucket al sistema de archivos del clúster Hadoop.

---

### Parte 2: Configuración del Servidor ElasticSearch

1. **Crear una instancia de VM para ElasticSearch**:
   - Utilizar Google Compute Engine para crear una nueva máquina virtual donde se instalará ElasticSearch.

2. **Instalar y configurar ElasticSearch**:
   - Instalar ElasticSearch en la VM y ajustar los parámetros necesarios, incluyendo la configuración de red para permitir conexiones externas.

3. **Configurar reglas de firewall**:
   - Abrir el puerto **9200** para permitir el acceso a ElasticSearch desde el clúster Hadoop y equipos locales.
   - Abrir el puerto **5601** para permitir el acceso a Kibana.

4. **Verificar la conexión**:
   - Desde el clúster Hadoop, comprobar que se puede acceder al servidor ElasticSearch.

---

### Parte 3: Configuración de la Conexión en el Clúster Hadoop

1. **Modificar la configuración de Hive**:
   - Editar el archivo `hive-site.xml` para incluir las propiedades necesarias para la conexión con ElasticSearch, como la dirección del servidor y el puerto.

2. **Añadir las librerías a Hive**:
   - Copiar los archivos JAR de `elasticsearch-hadoop` y `commons-httpclient` al directorio de librerías de Hive.

3. **Reiniciar el servicio de Hive**:
   - Reiniciar Hive para que reconozca las nuevas configuraciones y librerías.

---

### Parte 4: Conectar y Consultar Datos

1. **Crear un índice en ElasticSearch**:
   - Desde el servidor ElasticSearch, crear un nuevo índice que será utilizado para almacenar los datos.

2. **Agregar documentos al índice desde Hadoop**:
   - Utilizar el clúster Hadoop para insertar documentos en el índice recién creado en ElasticSearch.

3. **Consultar los datos**:
   - Verificar que los datos han sido correctamente insertados realizando consultas al índice desde el clúster Hadoop.

---

### Parte 5: Uso de Kibana (Opcional)

1. **Acceder a Kibana**:
   - Utilizar el puerto **5601** para acceder a la interfaz de Kibana desde un navegador web.

2. **Configurar un patrón de índice**:
   - En Kibana, crear un patrón de índice para el índice creado en ElasticSearch.

3. **Crear visualizaciones**:
   - Utilizar las herramientas de Kibana para crear visualizaciones y dashboards basados en los datos del índice.

---

## English

# Big Data Architecture: Integrating ElasticSearch and Hadoop

This project aims to configure the integration between a **Hadoop** cluster and **ElasticSearch**, enabling the combined use of these technologies for processing and analyzing large volumes of data.

### Table of Contents

- [Part 1: Setting Up ES-Hadoop](#part-1-setting-up-es-hadoop)
- [Part 2: Setting Up the ElasticSearch Server](#part-2-setting-up-the-elasticsearch-server)
- [Part 3: Configuring the Connection on the Hadoop Cluster](#part-3-configuring-the-connection-on-the-hadoop-cluster)
- [Part 4: Connecting and Querying Data](#part-4-connecting-and-querying-data)
- [Part 5: Using Kibana (Optional)](#part-5-using-kibana-optional)

---

### Part 1: Setting Up ES-Hadoop

1. **Create a Hadoop Cluster**:
   - Use Google Cloud Dataproc to create a standard or standalone Hadoop cluster.

2. **Download Required Libraries**:
   - Obtain the `elasticsearch-hadoop` and `commons-httpclient` JAR files.

3. **Create a Bucket in Google Cloud Storage**:
   - Store the downloaded JAR files in a bucket for easy access from the cluster.

4. **Upload JARs to the Hadoop Cluster**:
   - Copy the JAR files from the bucket to the Hadoop cluster's filesystem.

---

### Part 2: Setting Up the ElasticSearch Server

1. **Create a VM Instance for ElasticSearch**:
   - Use Google Compute Engine to create a new virtual machine where ElasticSearch will be installed.

2. **Install and Configure ElasticSearch**:
   - Install ElasticSearch on the VM and adjust the necessary parameters, including network settings to allow external connections.

3. **Configure Firewall Rules**:
   - Open port **9200** to allow access to ElasticSearch from the Hadoop cluster and local machines.
   - Open port **5601** to allow access to Kibana.

4. **Verify the Connection**:
   - From the Hadoop cluster, check that you can access the ElasticSearch server.

---

### Part 3: Configuring the Connection on the Hadoop Cluster

1. **Modify Hive Configuration**:
   - Edit the `hive-site.xml` file to include the necessary properties for connecting to ElasticSearch, such as the server address and port.

2. **Add Libraries to Hive**:
   - Copy the `elasticsearch-hadoop` and `commons-httpclient` JAR files to Hive's library directory.

3. **Restart Hive Service**:
   - Restart Hive to recognize the new configurations and libraries.

---

### Part 4: Connecting and Querying Data

1. **Create an Index in ElasticSearch**:
   - From the ElasticSearch server, create a new index that will be used to store data.

2. **Add Documents to the Index from Hadoop**:
   - Use the Hadoop cluster to insert documents into the newly created index in ElasticSearch.

3. **Query the Data**:
   - Verify that the data has been correctly inserted by performing queries on the index from the Hadoop cluster.

---

### Part 5: Using Kibana (Optional)

1. **Access Kibana**:
   - Use port **5601** to access the Kibana interface from a web browser.

2. **Configure an Index Pattern**:
   - In Kibana, create an index pattern for the index created in ElasticSearch.

3. **Create Visualizations**:
   - Use Kibana's tools to create visualizations and dashboards based on the index's data.

---

# Notas Finales / Final Notes

- **Seguridad / Security Considerations**:
  - Para fines de prueba, ElasticSearch puede haber sido configurado en modo inseguro. En un entorno de producción, asegúrate de implementar medidas de seguridad adecuadas.
  - For testing purposes, ElasticSearch may have been set to insecure mode. In a production environment, ensure proper security measures are in place.

- **Configuración de Firewall / Firewall Settings**:
  - Verifica que los puertos necesarios estén abiertos y correctamente configurados tanto en las reglas de firewall de Google Cloud como en los firewalls locales.
  - Make sure that the necessary ports are open and correctly configured both in Google Cloud firewall rules and local firewalls.

- **Compatibilidad de Versiones / Version Compatibility**:
  - Confirma que las versiones de Hadoop, ElasticSearch y las librerías utilizadas sean compatibles entre sí.
  - Verify that the versions of Hadoop, ElasticSearch, and the libraries used are compatible with each other.

---

# Agradecimientos / Acknowledgments

Gracias por seguir esta guía. Si tienes alguna pregunta o sugerencia, no dudes en contactarme.

Thank you for following this guide. If you have any questions or suggestions, feel free to reach out.

--- 
