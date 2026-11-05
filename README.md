# TAREA-05-11-2026
tarea de hoy
CREATE DATABASE HotelPatitas_Practica;
USE HotelPatitas_Practica;

CREATE TABLE Cliente AS
SELECT * FROM hotelpatitas.cliente;

CREATE TABLE Estancia AS
SELECT * FROM hotelpatitas.estancia;

CREATE TABLE EstanciaServicio AS
SELECT * FROM hotelpatitas.estanciaservicio;

CREATE TABLE Mascota AS
SELECT * FROM hotelpatitas.mascota;

CREATE TABLE Servicio AS
SELECT * FROM hotelpatitas.servicio;

ALTER TABLE Cliente
ADD PRIMARY KEY (id_cliente);

ALTER TABLE Estancia
ADD PRIMARY KEY (id_estancia);

ALTER TABLE EstanciaServicio
ADD PRIMARY KEY (id_estancia, id_servicio);

ALTER TABLE Mascota
ADD PRIMARY KEY (id_mascota);

ALTER TABLE Servicio
ADD PRIMARY KEY (id_servicio);

ALTER TABLE Cliente
MODIFY COLUMN id_cliente INT NOT NULL AUTO_INCREMENT;

ALTER TABLE Estancia
MODIFY COLUMN id_estancia INT NOT NULL AUTO_INCREMENT;

ALTER TABLE Mascota
MODIFY COLUMN id_mascota INT NOT NULL AUTO_INCREMENT;

ALTER TABLE Servicio
MODIFY COLUMN id_servicio INT NOT NULL AUTO_INCREMENT;

ALTER TABLE Mascota
ADD CONSTRAINT fk_cliente_mascota
FOREIGN KEY (id_cliente)
REFERENCES Cliente(id_cliente);

ALTER TABLE Estancia
ADD CONSTRAINT fk_estancia_servicio
FOREIGN KEY (id_servicio)
REFERENCES Servicio(id_servicio);

ALTER TABLE Cliente
ADD COLUMN correo VARCHAR(100);

ALTER TABLE Estancia
ADD COLUMN observaciones TEXT;

ALTER TABLE Mascota
MODIFY COLUMN peso DECIMAL(5,2);

ALTER TABLE Cliente
RENAME COLUMN telefono TO telefono_principal;

ALTER TABLE Mascota
ADD CONSTRAINT chk_peso
CHECK (peso > 0);

ALTER TABLE Cliente
ADD CONSTRAINT uq_correo
UNIQUE (correo);

ALTER TABLE Servicio
ADD CONSTRAINT chk_precio
CHECK (precio >= 0);

ALTER TABLE Estancia
ADD CONSTRAINT chk_fechas
CHECK (fecha_salida > fecha_entrada);

ALTER TABLE Servicio
ADD CONSTRAINT uq_nombre_servicio
UNIQUE (nombre);
